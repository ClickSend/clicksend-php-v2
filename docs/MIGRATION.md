# Migration Guide: clicksend/clicksend-php (legacy) → clicksend/clicksend-php (v2)

This guide helps you migrate from the legacy ClickSend PHP SDK to the current v2 SDK. **Both packages are published under the exact same Composer name, `clicksend/clicksend-php`** — there is no `-v2` suffix to disambiguate them on Packagist, so confirm which major version your `composer.json` is actually locked to before you start (check `composer.lock` / `composer show clicksend/clicksend-php`), and pin an explicit version constraint once you've migrated so Composer can't silently move you between them. The two SDKs are **not drop-in compatible** — class names, method names, request/response shapes, and parameter order/types have all changed. Read this guide fully before upgrading, then use the class/method mapping tables to update your code.

## Contents

1. [Why this migration isn't a drop-in replacement](#1-why-this-migration-isnt-a-drop-in-replacement)
2. [Installation & imports](#2-installation--imports)
3. [Authentication & client setup](#3-authentication--client-setup)
4. [Base path / URL changes](#4-base-path--url-changes)
5. [Method naming convention change](#5-method-naming-convention-change)
6. [Request payloads: `*Request` models replace reusable domain models](#6-request-payloads-request-models-replace-reusable-domain-models)
7. [Response payloads and the five generated call variants](#7-response-payloads-and-the-five-generated-call-variants)
8. [Error handling changes](#8-error-handling-changes)
9. [Async calls, per-call controls, and other new mechanics](#9-async-calls-per-call-controls-and-other-new-mechanics)
10. [Class-by-class mapping (all 37 legacy classes)](#10-class-by-class-mapping-all-37-legacy-classes)
11. [Side-by-side examples for common operations](#11-side-by-side-examples-for-common-operations)
12. [The Voice naming trap (read this before touching voice code)](#12-the-voice-naming-trap-read-this-before-touching-voice-code)
13. [Endpoints/methods removed in v2](#13-endpointsmethods-removed-in-v2)
14. [Brand-new resources and methods in v2](#14-brand-new-resources-and-methods-in-v2)
15. [Step-by-step migration checklist](#15-step-by-step-migration-checklist)

## 1. Why this migration isn't a drop-in replacement

The legacy SDK grew organically against ClickSend's v3 API: one API class per rough "concept" (e.g. `EmailMarketingApi`, `TransactionalEmailApi`, `MasterEmailTemplatesApi`, `UserEmailTemplatesApi`, `EmailDeliveryReceiptRulesApi` were five *separate* classes), method names followed a `resourcePath` + HTTP-verb pattern (`smsSendPost`, `smsHistoryGet`), and request bodies were broad reusable domain models (`SmsMessage`, `SmsMessageCollection`).

The v2 SDK is generated fresh from ClickSend's current OpenAPI v3 specification for PHP, which:

- Groups methods into **one class per resource/tag** — **26 classes instead of 37** (verified directly against `lib/Api/*.php` in both trees — not 29 as an earlier draft of this guide claimed). Several legacy classes were merged, one was split, and the Fax, Letters, and Postcards classes were dropped entirely — see [§13](#13-endpointsmethods-removed-in-v2).
- Names methods after the endpoint's **operationId** in camelCase (`sendSms`, `viewSmsHistory`, `exportSmsHistory`) instead of `resourcePath` + verb.
- Wraps every request body in a dedicated, single-purpose `*Request` model instead of reusing broad domain models — the `Model/` folder went from 47 concrete models to 383.
- Adds a leading `$content_type` parameter and a trailing `$contentType` content-negotiation parameter to every method, plus a fifth generated call variant (`operationNameRequest()`) that returns the raw unsent PSR-7 request.
- Models now implement `\JsonSerializable` in addition to `ArrayAccess`, and their internal metadata statics were renamed (`$swaggerTypes` → `$openAPITypes`, etc.).
- Requires **PHP 8.1+** (`composer.json`: `php: ">=7.4"` → `"^8.1"`), bumps `guzzlehttp/guzzle` to `^7.3`, and adds `guzzlehttp/psr7` as an explicit dependency.
- Patches the default `User-Agent` to `ClickSend-SDK/6.0.2/php` and the default `source` on SMS/MMS/voice message items to `'sdk-php'` (verified in `lib/Configuration.php` and the generated `*MessagesInner` models — see [§6](#6-request-payloads-request-models-replace-reusable-domain-models)).

None of this changes the underlying REST API — it's the same ClickSend v3 API — but it does change **every call site** in your existing integration.

## 2. Installation & imports

| | Legacy | v2 |
|---|---|---|
| Composer package | `clicksend/clicksend-php` | `clicksend/clicksend-php` — **same name**, confirm your lockfile is pinned to the version you intend |
| PHP required | `>=7.4` | `^8.1` |
| `guzzlehttp/guzzle` | `^7.4` | `^7.3` |
| `guzzlehttp/psr7` | not a direct dependency | `^1.7 \|\| ^2.0` (new direct dependency) |
| Namespace | `ClickSend\Api`, `ClickSend\Model` | `ClickSend\Api`, `ClickSend\Model` — **unchanged**, only the class names inside them changed |
| API classes | 37 | **26** (confirmed by listing `lib/Api/*.php` in the fresh v2 generation) |
| Model classes | 47 (+`ModelInterface`) | 383 (+`ModelInterface`) |

```bash
# Remove whatever version you currently have resolved
composer remove clicksend/clicksend-php

# Re-require, pinning to the v2 major/version you intend to run
composer require clicksend/clicksend-php:^6.0
```

> Because the package name did not change, a loose version constraint in `composer.json` could resolve to either SDK. Pin an explicit constraint and check `composer.lock` after installing to confirm you got the version you expect.

Class names inside the shared `ClickSend\Api` / `ClickSend\Model` namespaces changed — most acronym-heavy names dropped their all-caps styling and several narrow classes were folded into a bigger one:

```php
// Legacy
use ClickSend\Api\SMSApi;
use ClickSend\Api\MMSApi;
use ClickSend\ApiException;

// v2
use ClickSend\Api\SmsApi;
use ClickSend\Api\MmsApi;
use ClickSend\ApiException;   // same namespace/class name, see §8
```

See [§10](#10-class-by-class-mapping-all-37-legacy-classes) for the full class mapping.

## 3. Authentication & client setup

The building blocks are the same three pieces — a `Configuration`, a Guzzle HTTP client, and an `*Api` class — and construction is unchanged in shape:

```php
// Legacy
$config = ClickSend\Configuration::getDefaultConfiguration()
    ->setUsername(getenv('CLICKSEND_USERNAME'))
    ->setPassword(getenv('CLICKSEND_API_KEY'));

$apiInstance = new ClickSend\Api\SMSApi(new GuzzleHttp\Client(), $config);
```

```php
// v2 — identical shape, renamed class
$config = ClickSend\Configuration::getDefaultConfiguration()
    ->setUsername(getenv('CLICKSEND_USERNAME'))
    ->setPassword(getenv('CLICKSEND_API_KEY'));

$apiInstance = new ClickSend\Api\SmsApi(new GuzzleHttp\Client(), $config);
```

New `Configuration` methods worth knowing about (all confirmed present in `lib/Configuration.php`):

| Method | Purpose |
|---|---|
| `setCertFile()` / `getCertFile()`, `setKeyFile()` / `getKeyFile()` | client TLS certificate support |
| `setBooleanFormatForQueryString()` / `getBooleanFormatForQueryString()` | controls whether booleans serialize as `int` (`0`/`1`, default) or `string` (`"true"`/`"false"`) in query strings |
| `getHostSettings()`, `getHostString()`, `getHostFromSettings($index, $variables)` | multi-server/variable host scaffold (mirrors `setHostIndex()`/`getHostIndex()` on every API class — see [§9](#9-async-calls-per-call-controls-and-other-new-mechanics)); not currently meaningful for ClickSend's single host |

Default `User-Agent`: legacy used a generic Swagger-Codegen string; v2 defaults to `ClickSend-SDK/6.0.2/php` (`$userAgent` in `lib/Configuration.php`), overridable via `$config->setUserAgent('...')`.

## 4. Base path / URL changes

| | Legacy | v2 |
|---|---|---|
| Default host | `https://rest.clicksend.com/v3` | `https://rest.clicksend.com` |
| Per-method path | `/sms/send` (no version prefix — baked into the host) | `/v3/sms/send` (the `/v3` prefix is part of each method's path) |
| Override method | `$config->setHost(...)` | `$config->setHost(...)` (same method name) |

The final resolved URL is identical in both cases (`https://rest.clicksend.com/v3/sms/send`). This only matters if you've overridden `setHost()` to point at a proxy or mock server — if your custom host currently ends in `/v3` for the legacy SDK, **remove the `/v3` suffix** when you switch to v2, or you'll request `.../v3/v3/sms/send`.

## 5. Method naming convention change

Every method on every API class has been renamed. There is no shared prefix/suffix rule you can find-and-replace — the new names follow each endpoint's `operationId` (camelCased), which reads like an English phrase, while the old ones followed `resourcePath` + HTTP verb.

| Legacy | v2 |
|---|---|
| `smsSendPost` | `sendSms` |
| `smsHistoryGet` | `viewSmsHistory` |
| `smsHistoryExportGet` | `exportSmsHistory` |
| `smsTemplatesByTemplateIdDelete` | `deleteSmsTemplate` |
| `listsContactsByListIdPost` | `createNewContact` |
| `subaccountsPost` | `createSubaccount` |
| `voiceLangGet` | `viewVoiceLanguages` |
| `numbersSearchByCountryGet` | `viewAvailableNumbers` |

**You cannot mechanically derive the new name from the old one.** Use the mapping tables in [§10](#10-class-by-class-mapping-all-37-legacy-classes)–[§11](#11-side-by-side-examples-for-common-operations), or open the relevant `lib/Api/*.php` / `docs/Api/*.md` and search — the new names are descriptive enough that the right method is usually the first sensible match.

## 6. Request payloads: `*Request` models replace reusable domain models

Legacy methods took a broad, reusable domain model directly as the payload:

```php
// Legacy
use ClickSend\Model\SmsMessage;
use ClickSend\Model\SmsMessageCollection;

$smsMessage = new SmsMessage();
$smsMessage->setTo('+61411111111');
$smsMessage->setBody('Hello from ClickSend!');
$smsMessage->setSource('php');

$collection = new SmsMessageCollection();
$collection->setMessages([$smsMessage]);

$apiInstance->smsSendPost($collection);
```

v2 introduces **one dedicated `*Request` model per operation**, and — critically — every method's parameter list changed shape:

```php
// v2
use ClickSend\Model\SendSmsRequest;

$sendSmsRequest = new SendSmsRequest([
    'messages' => [
        ['to' => '+61411111111', 'body' => 'Hello from ClickSend!', 'source' => 'sdk'],
    ],
]);

// The first argument is the leading $content_type (pass null for the default);
// the request model is the SECOND argument.
$result = $apiInstance->sendSms(null, $sendSmsRequest);
```

Practical implications:

- **The old domain-model class names mostly don't exist in v2.** `SmsMessage`, `SmsMessageCollection`, `Email`, `Voice`, `Contact` (as a single reusable read/write model), `Subaccount`, etc. are gone. The `Model/` folder went from 47 concrete classes to 383, almost all named after a specific operation (`SendSmsRequest`, `CreateNewContactRequest`, `CreateSubaccountRequest`, …) rather than a domain noun. Nested list items get their own generated models too (e.g. `SendSmsRequestMessagesInner`).
- **Every v2 method's real signature is `operationName($content_type = null, $some_request = null, ..., string $contentType = self::contentTypes['operationName'][0])`.** There are *two* content-type-ish parameters and they are different things:
  - `$content_type` (snake_case, first positional parameter) — an optional literal value sent as the `Content-Type` request header override. Pass `null` for the default.
  - `$contentType` (camelCase, last parameter, always has a default) — internal content-negotiation control pulled from `self::contentTypes[...]`; you almost never need to touch it.
  - The actual request-body parameter (`$send_sms_request`, `$create_new_contact_request`, …) sits **between** them, in snake_case matching the model name.
  - **A previous draft of this guide showed a call like `sendSms(contentType: 'application/json', sendSmsRequest: $sendSmsRequest)` — both named-argument keys were wrong.** The real parameter names are snake_case (`content_type`, `send_sms_request`), not camelCase. Either call positionally — `$apiInstance->sendSms(null, $sendSmsRequest)`, as the v2 README does — or use the correct snake_case names as named arguments: `$apiInstance->sendSms(content_type: null, send_sms_request: $sendSmsRequest)`.
- **Some methods that take a resource ID gained a leading ID parameter that wasn't first before**, and its type changed. E.g. legacy `listsContactsByListIdPost($contact, $list_id)` (int `$list_id` *second*) → v2 `createNewContact($list_id, $content_type = null, $create_new_contact_request = null, ...)` (string `$list_id` *first* — confirmed via the generated docblocks: legacy is `@param int $list_id`, v2 is `@param string $list_id`).
- **Field names are unchanged in casing** — PHP models use `snake_case`/plain property names for JSON fields (`from`, `source`, `to`, `body`, …) via `getFrom()`/`setFrom()` accessors, so there is **no `_from`/`varFrom` collision** the way some other languages have (PHP has no `from` keyword clash). Confirmed directly in `Model/SendSmsRequestMessagesInner.php`: the property is `from`, accessed via `getFrom()`/`setFrom()`.
- **`source` now defaults to `'sdk-php'`** on SMS, MMS, and voice message items if you don't set it (legacy had no default) — confirmed in the generated constructor: `$this->setIfExists('source', $data ?? [], 'sdk-php')`.

## 7. Response payloads and the five generated call variants

Both SDKs return a parsed model on success and throw `ApiException` otherwise — that part hasn't changed. What's new in v2 is that **every operation now has five generated variants instead of four**:

| Variant | Behavior |
|---|---|
| `operationName()` | synchronous, returns the parsed response model |
| `operationNameWithHttpInfo()` | synchronous, returns `[$data, $statusCode, $headers]` |
| `operationNameAsync()` | returns a Guzzle promise |
| `operationNameAsyncWithHttpInfo()` | returns a Guzzle promise resolving to `[$data, $statusCode, $headers]` |
| `operationNameRequest()` | **new in v2** — returns the raw, unsent PSR-7 `Request` object, for inspecting/modifying the request yourself before sending it |

```php
// v2 — inspect the outgoing request before sending it
$request = $apiInstance->sendSmsRequest(null, $sendSmsRequest);
echo $request->getUri();
```

`setHostIndex()` / `getHostIndex()` are also new on every API class (multi-server support scaffold; not currently meaningful for ClickSend's single host).

## 8. Error handling changes

**This is largely unchanged, and confirmed so directly against source** — unlike some other ClickSend v2 SDKs, PHP v2 did **not** add status-specific exception subclasses.

| | Legacy | v2 |
|---|---|---|
| Class | `ClickSend\ApiException` | `ClickSend\ApiException` — same namespace, same class name |
| Base class | `\Exception` | `\Exception` |
| Methods | `getCode()`, `getMessage()` (inherited), `getResponseHeaders()`, `getResponseBody()`, `getResponseObject()` | same four `ApiException`-specific methods, confirmed identical in `lib/ApiException.php` |
| Subclasses | none | none — **no `BadRequestException`/`NotFoundException`-style subclasses exist in v2 PHP** |

```php
// Same pattern in both SDKs — only the API class/method names inside the try block change
try {
    $result = $apiInstance->sendSms(null, $sendSmsRequest);
} catch (ClickSend\ApiException $e) {
    $e->getCode();            // HTTP status code
    $e->getResponseBody();    // raw error payload from the API
    $e->getResponseHeaders(); // response headers
}
```

Update this only if you were introspecting model-specific fields on a caught exception's deserialized body (the shape of some response/error models changed — see [§6](#6-request-payloads-request-models-replace-reusable-domain-models)).

## 9. Async calls, per-call controls, and other new mechanics

Guzzle-promise async (`operationNameAsync()` / `operationNameAsyncWithHttpInfo()`) exists in **both** SDKs and works the same way — this was never removed, unlike the thread-pool `async_req` pattern in some other ClickSend language SDKs.

What's new in v2:

- **`operationNameRequest()`** — see [§7](#7-response-payloads-and-the-five-generated-call-variants).
- **`setHostIndex()` / `getHostIndex()`** on every API class and `Configuration::getHostSettings()` / `getHostFromSettings()` — multi-server scaffolding, unused today.
- **`Configuration::setBooleanFormatForQueryString()`** — controls how boolean query params serialize.
- **`Configuration::setCertFile()` / `setKeyFile()`** — client TLS cert support.
- Models implement `\JsonSerializable` (in addition to the pre-existing `ArrayAccess`), so `json_encode($model)` works directly without a manual `->__toString()`/`toArray()` call.
- Internal (de)serialization metadata statics were renamed: `$swaggerTypes` → `$openAPITypes`, `$swaggerFormats` → `$openAPIFormats`, `$swaggerModelName` → `$openAPIModelName` (with matching accessor renames `swaggerTypes()` → `openAPITypes()`, etc.). This only matters if you introspected these protected statics directly — public getters/setters (`getPhoneNumber()`, `setPhoneNumber()`, …) work the same way.
- `lib/FormDataProcessor.php` is new — a dedicated helper for building multipart form-data bodies, used internally by `UploadsApi::uploadAMediaFile()`. Purely additive; no calling-code change required.

## 10. Class-by-class mapping (all 37 legacy classes)

26 v2 classes now cover what used to be 37 legacy classes (confirmed by listing `lib/Api/*.php` in both trees — an earlier draft of this guide said "29", which was wrong). Several legacy classes merged (five email classes → one `EmailApi`); the Fax, Letters, and Postcards classes were **dropped entirely** (see [§13](#13-endpointsmethods-removed-in-v2)); and — critically — the two Voice classes **swapped roles** in v2 naming (see [§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code)).

| Legacy class | → | New class(es) | Notes |
|---|---|---|---|
| `AccountApi` | → | `ManagementApi`, `VerificationApi` | Split: `accountGet`/`accountUseageBySubaccountGet` → `ManagementApi`; `forgotPasswordPut`/`forgotUsernamePut` → `VerificationApi`. Four methods have no v2 equivalent — see [§13](#13-endpointsmethods-removed-in-v2). |
| `AccountRechargeApi` | → | `TransactionsApi` | Renamed 1:1 (6 methods). |
| `ContactApi` | → | `ContactsApi`, `ListsApi` | Split: single-contact-by-id CRUD → `ContactsApi`; list-scoped contact ops (create/list/copy/transfer/remove-opted-out) → `ListsApi`. |
| `ContactListApi` | → | `ListsApi` | Merged into `ListsApi`. |
| `CountriesApi` | → | `InternationalMessagingApi` | `countriesGet` → `listCountries`. |
| `DeliveryIssuesApi` | → | `MessageDeliveryApi` | Renamed. Unrelated to the delivery-*receipt-rule* classes despite the similar name. |
| `DetectAddressApi` | → | _(removed)_ | Address detection/parsing has no v2 equivalent — see [§13](#13-endpointsmethods-removed-in-v2). |
| `EmailDeliveryReceiptRulesApi` | → | `EmailApi` | Folded into the unified `EmailApi`. |
| `EmailMarketingApi` | → | `EmailApi` | Folded into the unified `EmailApi`. |
| `EmailToSmsApi` | → | `EmailToSmsApi` | Same class name, all 7 methods renamed. |
| `FAXApi` | → | _(removed)_ | Fax is not part of the v2 SDK — see [§13](#13-endpointsmethods-removed-in-v2). |
| `FAXDeliveryReceiptRulesApi` | → | _(removed)_ | Fax is not part of the v2 SDK — see [§13](#13-endpointsmethods-removed-in-v2). |
| `GlobalSendingApi` | → | `InternationalMessagingApi` | Folded in (`userCountries*` → `viewCountries` / `selectCountriesForGlobalSending` / `agreeToRulesAndRegulation`; `listCountriesGet` → `getCountriesForGlobalSending`). |
| `InboundFAXRulesApi` | → | _(removed)_ | Fax is not part of the v2 SDK — see [§13](#13-endpointsmethods-removed-in-v2). |
| `InboundSMSRulesApi` | → | `SmsApi` | Folded in as `*SmsInboundAutomation(s)`. |
| `MMSApi` | → | `MmsApi` | Renamed 1:1 for 4 methods; 2 dropped — see [§13](#13-endpointsmethods-removed-in-v2). |
| `MasterEmailTemplatesApi` | → | `EmailApi` | Folded into the unified `EmailApi`. |
| `MmsCampaignApi` | → | `MmsCampaignsApi` | Renamed 1:1 (6 methods). |
| `NumberApi` | → | `NumbersApi` | Renamed 1:1 (3 methods), plus a brand-new `registerNumbers` — see [§14](#14-brand-new-resources-and-methods-in-v2). **Not** `OwnNumbersApi` — that class has no legacy predecessor at all (see below). |
| `PostLetterApi` | → | _(removed)_ | Letters is not part of the v2 SDK — see [§13](#13-endpointsmethods-removed-in-v2). |
| `PostPostcardApi` | → | _(removed)_ | Postcards is not part of the v2 SDK — see [§13](#13-endpointsmethods-removed-in-v2). |
| `PostReturnAddressApi` | → | `AddressesApi` | Renamed (5 methods): `postReturnAddresses*` → `*ReturnAddress(es)`. |
| `ReferralAccountApi` | → | `ReferralsApi` | `referralAccountsGet` → `viewReferralAccounts`. |
| `ResellerAccountApi` | → | `ResellerApi` | Merged with `TransferCreditApi`. |
| `SMSApi` | → | `SmsApi` | Renamed 1:1 for all core methods. |
| `SMSDeliveryReceiptRulesApi` | → | `SmsApi` | Folded in as `*SmsDeliveryReceiptRule(s)`. |
| `SearchApi` | → | `ListsApi` | `searchContactsListsGet` → `viewContactLists` — **confirmed present** in `lib/Api/ListsApi.php`. An earlier draft of this guide claimed no v2 method matched `*search*` anywhere and to "confirm with ClickSend" — that was wrong; the method exists under this name. |
| `SmsCampaignApi` | → | `SmsCampaignsApi` | Renamed 1:1 (6 methods). |
| `StatisticsApi` | → | `StatisticsApi` | Same class name: `statisticsSmsGet` → `viewSmsStatistics`, `statisticsVoiceGet` → `viewVoiceStatistics`. |
| `SubaccountApi` | → | `SubaccountsApi` | Renamed 1:1 (6 methods). Pagination params dropped from `viewSubaccounts` — see [§11](#11-side-by-side-examples-for-common-operations). |
| `TimezonesApi` | → | `InternationalMessagingApi` | `timezonesGet` → `timezones`. |
| `TransactionalEmailApi` | → | `EmailApi` | Folded into the unified `EmailApi`. |
| `TransferCreditApi` | → | `ResellerApi` | Merged with `ResellerAccountApi`; `resellerTransferCreditPut` → `resellerTransferCredit`. |
| `UploadApi` | → | `UploadsApi` | `uploadsPost` → `uploadAMediaFile`. |
| `UserEmailTemplatesApi` | → | `EmailApi` | Folded into the unified `EmailApi`. |
| `VoiceApi` (send/history/price/lang) | → | **`VoiceMessagingApi`** | ⚠️ See [§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code) — this is *not* the new `VoiceApi`. 2 methods dropped — see [§13](#13-endpointsmethods-removed-in-v2). |
| `VoiceDeliveryReceiptRulesApi` | → | **`VoiceApi`** | ⚠️ See [§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code) — the new `VoiceApi` only has delivery-receipt-rule methods. |

`AlphaTagsApi`, `DefaultSendersApi`, `OwnNumbersApi`, and `UrlShorteningApi` in v2 have **no legacy predecessor at all** — see [§14](#14-brand-new-resources-and-methods-in-v2).

### Email: the five legacy classes → `EmailApi`

| Legacy | v2 (`EmailApi`) |
|---|---|
| `TransactionalEmailApi::emailSendPost` | `sendEmail` |
| `TransactionalEmailApi::emailHistoryGet` | `viewEmailHistory` |
| `TransactionalEmailApi::emailHistoryExportGet` | `exportEmailHistory` |
| `TransactionalEmailApi::emailPricePost` | `calculateEmailPrice` |
| `EmailMarketingApi::emailCampaignPost` | `sendEmailCampaign` |
| `EmailMarketingApi::emailCampaignsGet` | `viewAllEmailCampaigns` |
| `EmailMarketingApi::emailCampaignGet` | `viewEmailCampaign` |
| `EmailMarketingApi::emailCampaignPut` | `updateEmailCampaign` |
| `EmailMarketingApi::cancelEmailCampaignPut` | `cancelEmailCampaign` |
| `EmailMarketingApi::emailCampaignPricePost` | `calculateEmailCampaignPrice` |
| `EmailMarketingApi::emailCampaignHistoryGet` | `viewEmailCampaignHistory` |
| `EmailMarketingApi::emailCampaignHistoryExportGet` | `exportEmailCampaignHistory` |
| `EmailMarketingApi::allowedEmailAddressGet` | `viewAllowedEmailAddresses` |
| `EmailMarketingApi::allowedEmailAddressPost` | `createAllowedEmailAddress` |
| `EmailMarketingApi::specificAllowedEmailAddressGet` | `viewAllowedEmailAddress` |
| `EmailMarketingApi::specificAllowedEmailAddressDelete` | `deleteAllowedEmailAddress` |
| `EmailMarketingApi::verifyAllowedEmailAddressGet` | `verifyAllowedEmailAddress` |
| `EmailMarketingApi::sendVerificationTokenGet` | `sendEmailVerificationToken` |
| `UserEmailTemplatesApi::emailTemplatesGet` | `viewEmailTemplates` |
| `UserEmailTemplatesApi::emailTemplateGet` | `viewEmailTemplate` |
| `UserEmailTemplatesApi::emailTemplatePost` | `createEmailTemplate` |
| `UserEmailTemplatesApi::emailTemplatePut` | `updateEmailTemplate` |
| `UserEmailTemplatesApi::emailTemplateDelete` | `deleteEmailTemplate` |
| `MasterEmailTemplatesApi::masterEmailTemplatesGet` | `viewMasterEmailTemplates` |
| `MasterEmailTemplatesApi::masterEmailTemplateGet` | `viewMasterEmailTemplate` |
| `MasterEmailTemplatesApi::masterEmailTemplateCategoriesGet` | `viewTemplateCategories` |
| `MasterEmailTemplatesApi::masterEmailTemplateCategoryGet` | `viewTemplateCategory` |
| `MasterEmailTemplatesApi::masterEmailTemplatesInCategoryGet` | `viewTemplatesInCategory` |
| `EmailDeliveryReceiptRulesApi::emailDeliveryReceiptAutomationsGet` | `viewEmailDeliveryReceiptRules` |
| `EmailDeliveryReceiptRulesApi::emailDeliveryReceiptAutomationGet` | `viewEmailDeliveryReceiptRule` |
| `EmailDeliveryReceiptRulesApi::emailDeliveryReceiptAutomationPost` | `createEmailDeliveryReceiptRule` |
| `EmailDeliveryReceiptRulesApi::emailDeliveryReceiptAutomationPut` | `updateEmailDeliveryReceiptRule` |
| `EmailDeliveryReceiptRulesApi::emailDeliveryReceiptAutomationDelete` | `deleteEmailDeliveryReceiptRule` |

> `EmailMarketingApi::emailCampaignPut` in the legacy SDK reused an `EmailCampaign` model for update; v2's `updateEmailCampaign` takes an `UpdateEmailCampaignRequest`. Same story for every other method above — look up the specific request model for each call.

### SMS: `SMSApi` + `InboundSMSRulesApi` + `SMSDeliveryReceiptRulesApi` → `SmsApi`

| Legacy | v2 (`SmsApi`) |
|---|---|
| `SMSApi::smsSendPost` | `sendSms` |
| `SMSApi::smsHistoryGet` | `viewSmsHistory` |
| `SMSApi::smsHistoryExportGet` | `exportSmsHistory` |
| `SMSApi::smsPricePost` | `calculateSmsPrice` |
| `SMSApi::smsCancelAllPut` | `cancelAllSms` |
| `SMSApi::smsCancelByMessageIdPut` | `cancelSms` |
| `SMSApi::smsInboundGet` | `viewInboundSms` |
| `SMSApi::smsInboundPost` | `createTestInboundSms` |
| `SMSApi::smsInboundReadPut` | `markInboundSmsAsRead` |
| `SMSApi::smsInboundReadByMessageIdPut` | `markSpecificInboundSmsMessageAsRead` |
| `SMSApi::smsReceiptsGet` | `viewSmsReceipts` |
| `SMSApi::smsReceiptsByMessageIdGet` | `viewSpecificSmsReceipt` |
| `SMSApi::smsReceiptsPost` | `createTestSmsReceipt` |
| `SMSApi::smsReceiptsReadPut` | `markSmsReceiptAsRead` |
| `SMSApi::smsTemplatesGet` | `viewSmsTemplates` |
| `SMSApi::smsTemplatesPost` | `createSmsTemplate` |
| `SMSApi::smsTemplatesByTemplateIdPut` | `updateSmsTemplate` |
| `SMSApi::smsTemplatesByTemplateIdDelete` | `deleteSmsTemplate` |
| `InboundSMSRulesApi::smsInboundAutomationsGet` | `viewSmsInboundAutomations` |
| `InboundSMSRulesApi::smsInboundAutomationGet` | `viewSmsInboundAutomation` |
| `InboundSMSRulesApi::smsInboundAutomationPost` | `createSmsInboundAutomation` |
| `InboundSMSRulesApi::smsInboundAutomationPut` | `updateSmsInboundAutomation` |
| `InboundSMSRulesApi::smsInboundAutomationDelete` | `deleteSmsInboundAutomation` |
| `SMSDeliveryReceiptRulesApi::smsDeliveryReceiptAutomationsGet` | `viewSmsDeliveryReceiptRules` |
| `SMSDeliveryReceiptRulesApi::smsDeliveryReceiptAutomationGet` | `viewSmsDeliveryReceiptRule` |
| `SMSDeliveryReceiptRulesApi::smsDeliveryReceiptAutomationPost` | `createSmsDeliveryReceiptRule` |
| `SMSDeliveryReceiptRulesApi::smsDeliveryReceiptAutomationPut` | `updateSmsDeliveryReceiptRule` |
| `SMSDeliveryReceiptRulesApi::smsDeliveryReceiptAutomationDelete` | `deleteSmsDeliveryReceiptRule` |
| — | `viewASpecificSmsTemplate` *(new — see [§14](#14-brand-new-resources-and-methods-in-v2))* |
| — | `viewASpecificInboundSmsMessage` *(new — see [§14](#14-brand-new-resources-and-methods-in-v2))* |

### Contacts & lists: `ContactApi` + `ContactListApi` + `SearchApi` → `ContactsApi` + `ListsApi`

| Legacy | v2 |
|---|---|
| `ContactApi::listsContactsByListIdAndContactIdGet` | `ContactsApi::getSpecificContact` |
| `ContactApi::listsContactsByListIdAndContactIdPut` | `ContactsApi::updateContact` |
| `ContactApi::listsContactsByListIdAndContactIdDelete` | `ContactsApi::deleteContact` |
| `ContactApi::listsContactsByListIdPost` | `ListsApi::createNewContact` |
| `ContactApi::listsContactsByListIdGet` | `ListsApi::viewListContacts` |
| `ContactApi::listsCopyContactPut` | `ListsApi::copyContactToList` |
| `ContactApi::listsTransferContactPut` | `ListsApi::transferContactToList` |
| `ContactApi::listsRemoveOptedOutContactsByListIdAndOptOutListIdPut` | `ListsApi::removeOptedOutContacts` |
| `ContactListApi::listsGet` | `ListsApi::viewLists` |
| `ContactListApi::listsPost` | `ListsApi::createList` |
| `ContactListApi::listsByListIdGet` | `ListsApi::viewSpecificList` |
| `ContactListApi::listsByListIdPut` | `ListsApi::updateList` |
| `ContactListApi::listsByListIdDelete` | `ListsApi::deleteList` |
| `ContactListApi::listsImportByListIdPost` | `ListsApi::importContacts` |
| `ContactListApi::listsRemoveDuplicatesByListIdPut` | `ListsApi::removeDuplicateContacts` |
| `SearchApi::searchContactsListsGet` | `ListsApi::viewContactLists` |

### Account & billing

| Legacy | v2 |
|---|---|
| `AccountApi::accountGet` | `ManagementApi::viewAccountDetails` |
| `AccountApi::accountUseageBySubaccountGet` | `ManagementApi::viewAccountUsage` |
| `AccountApi::forgotPasswordPut` | `VerificationApi::forgotPassword` |
| `AccountApi::forgotUsernamePut` | `VerificationApi::forgotUsername` |
| `AccountRechargeApi::rechargeCreditCardGet` | `TransactionsApi::currentPaymentInfo` |
| `AccountRechargeApi::rechargeCreditCardPut` | `TransactionsApi::updatePaymentInfo` |
| `AccountRechargeApi::rechargePackagesGet` | `TransactionsApi::viewRechargePackages` |
| `AccountRechargeApi::rechargePurchaseByPackageIdPut` | `TransactionsApi::purchaseRechargePackage` |
| `AccountRechargeApi::rechargeTransactionsGet` | `TransactionsApi::viewAllTransactions` |
| `AccountRechargeApi::rechargeTransactionsByTransactionIdGet` | `TransactionsApi::viewSpecificTransaction` |
| `ResellerAccountApi::resellerAccountsGet` | `ResellerApi::viewClientAccounts` |
| `ResellerAccountApi::resellerAccountsPost` | `ResellerApi::createResellerAccount` |
| `ResellerAccountApi::resellerAccountsByClientUserIdGet` | `ResellerApi::viewSpecificClientAccount` |
| `ResellerAccountApi::resellerAccountsByClientUserIdPut` | `ResellerApi::updateClientAccount` |
| `TransferCreditApi::resellerTransferCreditPut` | `ResellerApi::resellerTransferCredit` |
| `SubaccountApi::subaccountsGet` | `SubaccountsApi::viewSubaccounts` |
| `SubaccountApi::subaccountsPost` | `SubaccountsApi::createSubaccount` |
| `SubaccountApi::subaccountsBySubaccountIdGet` | `SubaccountsApi::viewSpecificSubaccount` |
| `SubaccountApi::subaccountsBySubaccountIdPut` | `SubaccountsApi::updateSubaccount` |
| `SubaccountApi::subaccountsBySubaccountIdDelete` | `SubaccountsApi::deleteSubaccount` |
| `SubaccountApi::subaccountsRegenApiKeyBySubaccountIdPut` | `SubaccountsApi::generateNewApiKey` |
| `ReferralAccountApi::referralAccountsGet` | `ReferralsApi::viewReferralAccounts` |

### Numbers, addresses, uploads, international, delivery issues

| Legacy | v2 |
|---|---|
| `NumberApi::numbersGet` | `NumbersApi::viewYourNumbers` |
| `NumberApi::numbersSearchByCountryGet` | `NumbersApi::viewAvailableNumbers` |
| `NumberApi::numbersBuyByDedicatedNumberPost` | `NumbersApi::purchaseDedicatedNumber` |
| `PostReturnAddressApi::postReturnAddressesGet` | `AddressesApi::viewYourReturnAddresses` |
| `PostReturnAddressApi::postReturnAddressesPost` | `AddressesApi::createReturnAddress` |
| `PostReturnAddressApi::postReturnAddressesByReturnAddressIdGet` | `AddressesApi::viewSpecificReturnAddress` |
| `PostReturnAddressApi::postReturnAddressesByReturnAddressIdPut` | `AddressesApi::updateReturnAddress` |
| `PostReturnAddressApi::postReturnAddressesByReturnAddressIdDelete` | `AddressesApi::deleteReturnAddress` |
| `UploadApi::uploadsPost` | `UploadsApi::uploadAMediaFile` |
| `CountriesApi::countriesGet` | `InternationalMessagingApi::listCountries` |
| `TimezonesApi::timezonesGet` | `InternationalMessagingApi::timezones` |
| `GlobalSendingApi::listCountriesGet` | `InternationalMessagingApi::getCountriesForGlobalSending` |
| `GlobalSendingApi::userCountriesGet` | `InternationalMessagingApi::viewCountries` |
| `GlobalSendingApi::userCountriesPost` | `InternationalMessagingApi::selectCountriesForGlobalSending` |
| `GlobalSendingApi::userCountriesAgreePost` | `InternationalMessagingApi::agreeToRulesAndRegulation` |
| `DeliveryIssuesApi::deliveryIssuesGet` | `MessageDeliveryApi::getAllDeliveryIssues` |
| `DeliveryIssuesApi::deliveryIssuesPost` | `MessageDeliveryApi::createDeliveryIssue` |

### MMS, campaigns, voice, statistics

| Legacy | v2 |
|---|---|
| `MMSApi::mmsSendPost` | `MmsApi::sendMms` |
| `MMSApi::mmsHistoryGet` | `MmsApi::viewMmsHistory` |
| `MMSApi::mmsHistoryExportGet` | `MmsApi::exportMmsHistory` |
| `MMSApi::mmsPricePost` | `MmsApi::calculateMmsPrice` |
| `MmsCampaignApi::mmsCampaignsSendPost` | `MmsCampaignsApi::sendMmsCampaign` |
| `MmsCampaignApi::mmsCampaignsGet` | `MmsCampaignsApi::viewAllMmsCampaigns` |
| `MmsCampaignApi::mmsCampaignByMmsCampaignIdGet` | `MmsCampaignsApi::viewMmsCampaign` |
| `MmsCampaignApi::mmsCampaignsByMmsCampaignIdPut` | `MmsCampaignsApi::updateMmsCampaign` |
| `MmsCampaignApi::mmsCampaignsCancelByMmsCampaignIdPut` | `MmsCampaignsApi::cancelMmsCampaign` |
| `MmsCampaignApi::mmsCampaignsPricePost` | `MmsCampaignsApi::calculateMmsCampaignPrice` |
| `SmsCampaignApi::smsCampaignsSendPost` | `SmsCampaignsApi::sendSmsCampaign` |
| `SmsCampaignApi::smsCampaignsGet` | `SmsCampaignsApi::viewSmsCampaigns` |
| `SmsCampaignApi::smsCampaignBySmsCampaignIdGet` | `SmsCampaignsApi::viewSpecificSmsCampaign` |
| `SmsCampaignApi::smsCampaignsBySmsCampaignIdPut` | `SmsCampaignsApi::updateSmsCampaign` |
| `SmsCampaignApi::smsCampaignsCancelBySmsCampaignIdPut` | `SmsCampaignsApi::cancelSmsCampaign` |
| `SmsCampaignApi::smsCampaignsPricePost` | `SmsCampaignsApi::calculateSmsCampaignPrice` |
| `VoiceApi::voiceSendPost` (legacy class) | `VoiceMessagingApi::sendVoiceMessage` ⚠️ [§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code) |
| `VoiceApi::voiceHistoryGet` (legacy class) | `VoiceMessagingApi::getVoiceHistory` |
| `VoiceApi::voiceHistoryExportGet` (legacy class) | `VoiceMessagingApi::exportVoiceHistory` |
| `VoiceApi::voicePricePost` (legacy class) | `VoiceMessagingApi::calculateVoicePrice` |
| `VoiceApi::voiceLangGet` (legacy class) | `VoiceMessagingApi::viewVoiceLanguages` |
| `VoiceApi::voiceCancelAllPut` (legacy class) | `VoiceMessagingApi::cancelAllVoiceMessages` |
| `VoiceApi::voiceCancelByMessageIdPut` (legacy class) | `VoiceMessagingApi::cancelVoiceMessage` |
| `VoiceApi::voiceReceiptsGet` (legacy class) | `VoiceMessagingApi::viewVoiceReceipts` |
| `VoiceDeliveryReceiptRulesApi::voiceDeliveryReceiptAutomationsGet` | `VoiceApi::viewVoiceDeliveryReceiptRules` ⚠️ [§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code) |
| `VoiceDeliveryReceiptRulesApi::voiceDeliveryReceiptAutomationGet` | `VoiceApi::viewVoiceDeliveryReceiptRule` |
| `VoiceDeliveryReceiptRulesApi::voiceDeliveryReceiptAutomationPost` | `VoiceApi::createVoiceDeliveryReceiptRule` |
| `VoiceDeliveryReceiptRulesApi::voiceDeliveryReceiptAutomationPut` | `VoiceApi::updateVoiceDeliveryReceiptRule` |
| `VoiceDeliveryReceiptRulesApi::voiceDeliveryReceiptAutomationDelete` | `VoiceApi::deleteVoiceDeliveryReceiptRule` |
| `StatisticsApi::statisticsSmsGet` | `StatisticsApi::viewSmsStatistics` |
| `StatisticsApi::statisticsVoiceGet` | `StatisticsApi::viewVoiceStatistics` |

### Email-to-SMS: `EmailToSmsApi` → `EmailToSmsApi`

| Legacy | v2 |
|---|---|
| `smsEmailSmsGet` | `viewAllowedEmails` |
| `smsEmailSmsPost` | `addAllowedEmail` |
| `smsEmailSmsStrippedStringPost` | `createStrippedStringRule` |
| `smsEmailSmsStrippedStringGet` | `viewStrippedStringRule` |
| `smsEmailSmsStrippedStringsGet` | `viewStrippedStringRules` |
| `smsEmailSmsStrippedStringPut` | `updateStrippedStringRule` |
| `smsEmailSmsStrippedStringDelete` | `deleteStrippedStringRule` |

## 11. Side-by-side examples for common operations

### Send an SMS

```php
// Legacy
use ClickSend\Model\SmsMessage;
use ClickSend\Model\SmsMessageCollection;

$msg = new SmsMessage();
$msg->setTo('+61411111111');
$msg->setBody('Hello from ClickSend!');
$msg->setSource('php');

$collection = new SmsMessageCollection();
$collection->setMessages([$msg]);

try {
    $result = $apiInstance->smsSendPost($collection);
    print_r($result);
} catch (ClickSend\ApiException $e) {
    echo $e->getCode(), ' ', $e->getResponseBody();
}

// v2
use ClickSend\Model\SendSmsRequest;

$sendSmsRequest = new SendSmsRequest([
    'messages' => [
        ['to' => '+61411111111', 'body' => 'Hello from ClickSend!', 'source' => 'sdk'],
    ],
]);

try {
    // content_type first (null = default), the request model second
    $result = $apiInstance->sendSms(null, $sendSmsRequest);
    print_r($result);
} catch (ClickSend\ApiException $e) {
    echo $e->getCode(), ' ', $e->getResponseBody();
}
```

### View SMS history

```php
// Legacy
$smsApi->smsHistoryGet($q, $dateFrom, $dateTo, $page, $limit);

// v2 — content_type is now the leading param, order_by is new, limit has a bound
$smsApi->viewSmsHistory(
    null,               // content_type
    $page, $limit, $q, 'date:desc',
    $dateFrom, $dateTo,
);
```

> Confirmed via the generated signatures: legacy is `smsHistoryGet($q, $date_from, $date_to, $page, $limit)`, v2 is `viewSmsHistory($content_type, $page, $limit, $q, $order_by, $date_from, $date_to, ...)`. The parameter *order* changed, not just the names — pass by name (`viewSmsHistory(page: $page, limit: $limit, q: $q, ...)`) to avoid mis-ordered positional calls.

### Send an MMS / Email / Voice message

Same pattern on every channel — build a `Send<Channel>Request`, call `send<Channel>(null, $request)`:

| Channel | Legacy call | v2 call |
|---|---|---|
| MMS | `$mmsApi->mmsSendPost($mmsMessageCollection)` | `$mmsApi->sendMms(null, $sendMmsRequest)` |
| Email | `$emailApi->emailSendPost($email)` | `$emailApi->sendEmail(null, $sendEmailRequest)` |
| Voice | `$voiceApi->voiceSendPost($voiceCollection)` (legacy `VoiceApi`) | `$voiceMessagingApi->sendVoiceMessage(null, $sendVoiceMessageRequest)` (⚠️ new `VoiceMessagingApi`, see [§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code)) |

> **Fax, Letters, and Postcards are not part of the v2 SDK** — there is no `sendFax` / `postLettersSendPost` / `postPostcardsSendPost` equivalent. See [§13](#13-endpointsmethods-removed-in-v2).

### Create a contact in a list

```php
// Legacy — contact model FIRST, int $list_id SECOND
$contactApi->listsContactsByListIdPost($contact, $listId);

// v2 — $list_id is now FIRST and a STRING; content_type second; payload third
$listsApi->createNewContact((string) $listId, null, $createNewContactRequest);
```

> Confirmed via the generated docblocks: legacy `listsContactsByListIdPost($contact, $list_id)` documents `$list_id` as `@param int`; v2 `createNewContact($list_id, $content_type = null, $create_new_contact_request = null, ...)` documents `$list_id` as `@param string`. Cast explicitly when migrating.

### List contacts / lists — pagination parameters were dropped

```php
// Legacy — page / limit / updated_after were real parameters
$contactApi->listsContactsByListIdGet($listId, $page, $limit, $updatedAfter);
$contactListApi->listsGet($page, $limit);
$subaccountApi->subaccountsGet($page, $limit);

// v2 — those params no longer exist on the signature
$listsApi->viewListContacts((string) $listId);
$listsApi->viewLists();
$subaccountsApi->viewSubaccounts();
```

**This is a real behavior change, not just a rename.** Confirmed directly against the generated signatures: v2 `viewLists($content_type = null, ...)`, `viewListContacts($list_id, $content_type = null, ...)`, and `viewSubaccounts($content_type = null, ...)` take no `page` / `limit` / `updated_after`. Verify against the current API reference how pagination is handled for any workflow that relied on them before you ship.

### Create a subaccount

```php
// Legacy
$subaccountApi->subaccountsPost($subaccount);

// v2
$subaccountsApi->createSubaccount(null, $createSubaccountRequest);
```

## 12. The Voice naming trap (read this before touching voice code)

This is the single most confusing rename in the whole migration, and a naive search-and-replace of `VoiceApi` will silently point your code at the wrong class:

- Legacy **`VoiceApi`** (send a voice message, view/export history, calculate price, list voice languages, cancel, view receipts) → renamed to new **`VoiceMessagingApi`**.
- Legacy **`VoiceDeliveryReceiptRulesApi`** (create/update/delete/view delivery-receipt rules) → renamed to new **`VoiceApi`**.

The new `VoiceApi` has **nothing to do with sending voice calls** — it is purely the old delivery-receipt-rules class under a new name. Confirmed directly: `lib/Api/VoiceApi.php` in v2 contains exactly five methods — `createVoiceDeliveryReceiptRule`, `deleteVoiceDeliveryReceiptRule`, `updateVoiceDeliveryReceiptRule`, `viewVoiceDeliveryReceiptRule`, `viewVoiceDeliveryReceiptRules` — and nothing else. To migrate voice-sending code, import `VoiceMessagingApi`:

```php
// Wrong — this runs, but VoiceApi in v2 only has delivery-receipt-rule methods
$voiceApi = new ClickSend\Api\VoiceApi(new GuzzleHttp\Client(), $config);
$voiceApi->sendVoiceMessage(...);          // Fatal error: Call to undefined method

// Correct
$voiceMessagingApi = new ClickSend\Api\VoiceMessagingApi(new GuzzleHttp\Client(), $config);
$voiceMessagingApi->sendVoiceMessage(null, $sendVoiceMessageRequest);
```

## 13. Endpoints/methods removed in v2

### Entire products dropped

The **Fax**, **Letters**, and **Postcards** products have **no presence at all** in the v2 SDK — no API class, no models. If your integration sends faxes, letters, or postcards, there is currently no v2 SDK path for it; call the REST API directly or stay on the legacy SDK for those channels.

| Legacy class(es) | Covered (legacy) | v2 |
|---|---|---|
| `FAXApi`, `FAXDeliveryReceiptRulesApi`, `InboundFAXRulesApi` | send fax, fax history/export, fax price, fax receipts, fax delivery-receipt rules, inbound fax rules | _none_ |
| `PostLetterApi` | send letter (`postLettersSendPost`), letter history (`postLettersHistoryGet`), export (`postLettersExportGet`), price (`postLettersPricePost`) | _none_ |
| `PostPostcardApi` | send postcard (`postPostcardsSendPost`), postcard history/export, postcard price | _none_ |
| `DetectAddressApi` | address detection/parsing (`detectAddressPost`) | _none_ |

### Individual methods dropped (class otherwise survived)

The following legacy operations have **no equivalent anywhere in the v2 SDK**. If your integration depends on any of these, check the current ClickSend API reference before upgrading — the underlying endpoint may have been retired, moved, or simply not covered by the new spec at build time:

- `AccountApi::accountPost` — update account details
- `AccountApi::accountVerifySendPut` — send account verification email
- `AccountApi::accountVerifyVerifyByActivationTokenPut` — verify account by activation token
- `AccountApi::forgotPasswordVerifyPut` — verify a forgotten-password token
- `MMSApi::mmsReceiptsGet` — view MMS delivery receipts
- `MMSApi::mmsReceiptsReadPut` — mark MMS receipts as read
- `VoiceApi::voiceReceiptsPost` (legacy class) — create a test voice receipt
- `VoiceApi::voiceReceiptsReadPut` (legacy class) — mark voice receipts as read

Additionally, **pagination parameters (`page`, `limit`, `updated_after`) were dropped** from several method signatures even where the class survived — notably `ListsApi::viewLists`, `ListsApi::viewListContacts`, and `SubaccountsApi::viewSubaccounts` (see [§11](#11-side-by-side-examples-for-common-operations)).

## 14. Brand-new resources and methods in v2

No legacy counterpart at all — nothing to migrate, but worth knowing they exist (all confirmed present in `lib/Api/` of the fresh v2 generation):

- **`AlphaTagsApi`** — `listAlphaTags`, `getAlphaTag`, `requestAlphaTag`, `deleteAlphaTag`
- **`DefaultSendersApi`** — `getDefaultSendersList`, `getDefaultSenderDetails`, `createDefaultSender`, `updateDefaultSender`, `deleteDefaultSender`, `listCompliantSenderTypes`
- **`OwnNumbersApi`** (Bring Your Own Number) — `listOwnNumbers`, `getOwnNumberDetail`, `updateOwnNumber`, `deleteOwnNumber`, `requestOwnNumberVerificationOtp`, `verifyOwnNumberOtp`
- **`UrlShorteningApi`** — `shortUrlGetStatistics`, `shortUrlGetTracking`
- **`NumbersApi::registerNumbers`** — number registration (alongside the renamed `NumberApi` methods)
- **`SmsApi::viewASpecificInboundSmsMessage`** and **`SmsApi::viewASpecificSmsTemplate`** — fetch a single inbound message / template by ID (legacy only exposed the list endpoints)
- **`VerificationApi`** — hosts the account-recovery methods split out of legacy `AccountApi` (`forgotPassword`, `forgotUsername`); the class itself is new even though its two methods have legacy predecessors (see [§10](#10-class-by-class-mapping-all-37-legacy-classes))

## 15. Step-by-step migration checklist

1. **Confirm your Composer resolution.** The package name didn't change (`clicksend/clicksend-php` for both) — check `composer.lock` / `composer show clicksend/clicksend-php` before assuming which version you're running, then pin an explicit version constraint ([§2](#2-installation--imports)).
2. **Bump to PHP 8.1+** and update `guzzlehttp/guzzle` to `^7.3`; `guzzlehttp/psr7` becomes a direct dependency.
3. **Rename every API class you instantiate** (`SMSApi` → `SmsApi`, `MMSApi` → `MmsApi`, `ContactApi`/`ContactListApi`/`SearchApi` → `ContactsApi`/`ListsApi`, …) using the [§10](#10-class-by-class-mapping-all-37-legacy-classes) table. **Pay special attention to `VoiceApi` → `VoiceMessagingApi`** ([§12](#12-the-voice-naming-trap-read-this-before-touching-voice-code)) — the new `VoiceApi` is a different class entirely.
4. **Rename every method call** using the [§10](#10-class-by-class-mapping-all-37-legacy-classes)/[§11](#11-side-by-side-examples-for-common-operations) tables or the generated `docs/Api/*.md`.
5. **Rebuild every request payload** with the matching `*Request` model instead of the old shared domain model ([§6](#6-request-payloads-request-models-replace-reusable-domain-models)).
6. **Fix every call's argument list, not just the payload.** Every v2 method takes a leading `$content_type` (pass `null`) before the request model, and IDs like `$list_id` moved to the front and changed from `int` to `string` on several methods. **If you're porting named-argument calls, use snake_case keys** (`content_type:`, `send_sms_request:`) — camelCase named-argument keys silently miss the real parameters ([§6](#6-request-payloads-request-models-replace-reusable-domain-models), [§11](#11-side-by-side-examples-for-common-operations)).
7. **Re-check parameters for every call** — several methods reordered args, changed types, added params (`order_by`), or dropped pagination params entirely ([§11](#11-side-by-side-examples-for-common-operations), [§13](#13-endpointsmethods-removed-in-v2)).
8. **Error handling needs no structural change** — `ClickSend\ApiException` kept its namespace, base class, and methods, and v2 did not add status-specific subclasses. Update only if you inspect model-specific fields on the deserialized error body ([§8](#8-error-handling-changes)).
9. **Check for removed endpoints and dropped products** ([§13](#13-endpointsmethods-removed-in-v2)) — the entire Fax, Letters, and Postcards products are gone — and confirm a replacement exists in the current API before shipping.
10. **If you rely on Guzzle-promise async (`*Async()`/`*AsyncWithHttpInfo()`), no change is needed** beyond the method rename — this mechanism exists unchanged in both SDKs.
11. **Test each migrated call against ClickSend sandbox/test credentials** before deploying. PHP won't catch a renamed method or reordered argument until runtime, so smoke-test every endpoint your integration uses.
