# Migration Guide: clicksend-php v1 → clicksend-php-v2

This guide covers migrating from the legacy [`clicksend/clicksend-php`](https://github.com/ClickSend/clicksend-php) SDK to this repository, [`clicksend/clicksend-php-v2`](https://github.com/ClickSend/clicksend-php-v2).

This is a **major, breaking rewrite**. Almost nothing is a drop-in replacement — API class names, method names, and model classes have all changed. Treat this as adopting a new SDK, not upgrading an existing one.

## At a glance

| | Old SDK (v1) | New SDK (v2) |
|---|---|---|
| Composer package | `clicksend/clicksend-php` | `clicksend/clicksend-php` |
| PHP version | `>=7.4` | `^8.1` |
| HTTP client deps | `guzzlehttp/guzzle: ^7.4` | `guzzlehttp/guzzle: ^7.3` **plus new** `guzzlehttp/psr7: ^1.7 \|\| ^2.0` |
| Default host | `https://rest.clicksend.com/v3` | `https://rest.clicksend.com` (`/v3` prefix moved into each method's path) |
| API classes | 37 | 26 |
| Model classes | 48 | 384 |
| Generated docs files | 84 (37 Api + 47 Model) | 409 (26 Api + 383 Model) |
| Auth | HTTP Basic (username + API key) | HTTP Basic (username + API key) — unchanged |
| Namespace | `ClickSend\Api`, `ClickSend\Model` | `ClickSend\Api`, `ClickSend\Model` — unchanged |

## Why so many more model classes?

The old SDK reused a small number of shared models (e.g. one `Contact` class for create, update, and read). The new SDK generates a **dedicated model per request/response payload** — e.g. `CreateNewContactRequest`, `Contact` (read), and per-operation request models are now distinct classes instead of one shared `Contact`. This is why the model count jumped from 48 to 384. Expect to look up the exact request model class for each call rather than reusing one object across operations.

## 1. Installation & requirements

- Bump your project to **PHP 8.1+**.
- Requirement changes in `composer.json`:
  - `php`: `>=7.4` → `^8.1`
  - `guzzlehttp/guzzle`: `^7.4` → `^7.3`
  - added `guzzlehttp/psr7`: `^1.7 || ^2.0`
- The package name is unchanged (`clicksend/clicksend-php`), so if you're pointing Composer at this new repo directly (rather than a future Packagist release), update your `composer.json` `repositories`/`require` entry accordingly rather than expecting a version bump to pull it in automatically.

## 2. Authentication & client configuration

Credential setup is the same shape (HTTP Basic, username + API key):

```php
$config = ClickSend\Configuration::getDefaultConfiguration()
    ->setUsername(getenv('CLICKSEND_USERNAME'))
    ->setPassword(getenv('CLICKSEND_API_KEY'));
```

New optional `Configuration` methods worth knowing about:
- `setCertFile()` / `setKeyFile()` — client TLS cert support.
- `setBooleanFormatForQueryString()` / `getBooleanFormatForQueryString()` — controls whether booleans serialize as `int` (`0`/`1`, default) or `string` (`"true"`/`"false"`) in query strings.
- `getHostSettings()` / `getHostFromSettings($index, $variables)` — multi-server/variable host support (mirrors new `setHostIndex()`/`getHostIndex()` on every API class), unused by ClickSend today since there's a single host, but present in the generated surface.

### Base path / host change

The default host changed, though the final resolved URL is identical:

| | v1 | v2 |
|---|---|---|
| `Configuration::$host` | `https://rest.clicksend.com/v3` | `https://rest.clicksend.com` |
| Per-method `$resourcePath` | `/sms/send` | `/v3/sms/send` |

You only need to act on this if you call `Configuration::setHost()` with a custom base URL (proxy, mock server, regional endpoint). If that override currently ends in `/v3`, **drop the `/v3` suffix** when moving to v2 — otherwise requests resolve to `.../v3/v3/...`. Any test fixtures or URL assertions that hard-code the old host need the same adjustment.

### User-Agent

The default `User-Agent` changed from `ClickSend-Codegen/1.0.0/php` to a version-stamped `ClickSend-SDK/<version>/php` (e.g. `ClickSend-SDK/6.0.1/php`). Override it with `Configuration::setUserAgent()` as before if you depend on a specific value.

## 3. API class renames and consolidation

Class names dropped the all-caps acronyms and several narrow "rules"/"list" classes were **folded into their parent domain class**. Method names changed from REST-path-derived names (`resourcePath` + HTTP verb, e.g. `smsSendPost`, `smsHistoryGet`, `smsHistoryExportGet`) to each endpoint's **operationId**, which reads as a verb-first action name (`sendSms`, `viewSmsHistory`, `exportSmsHistory`). There is no mechanical find/replace rule — look each one up.

| Old class | New class / notes |
|---|---|
| `SMSApi` | `SmsApi` (now also includes SMS delivery receipt rules, inbound rules, and SMS templates) |
| `SMSDeliveryReceiptRulesApi` | merged into `SmsApi` (e.g. `createSmsDeliveryReceiptRule`) |
| `InboundSMSRulesApi` | merged into `SmsApi` (e.g. `createSmsInboundAutomation`) |
| `MMSApi` | `MmsApi` |
| `MmsCampaignApi` | `MmsCampaignsApi` |
| `FAXApi` | **removed** — Fax is not part of v2 (see note below this table) |
| `FAXDeliveryReceiptRulesApi` | **removed** — Fax is not part of v2 |
| `InboundFAXRulesApi` | **removed** — Fax is not part of v2 |
| `VoiceApi` (send / history / export / price / languages / receipts / cancel) | **`VoiceMessagingApi`** — ⚠️ renamed, *not* the new `VoiceApi`. See the Voice naming trap below. |
| `VoiceDeliveryReceiptRulesApi` | **`VoiceApi`** — ⚠️ the new `VoiceApi` holds *only* delivery-receipt-rule methods. See the Voice naming trap below. |
| `TransactionalEmailApi` | `EmailApi` |
| `EmailMarketingApi` | `EmailApi` |
| `EmailDeliveryReceiptRulesApi` | merged into `EmailApi` |
| `MasterEmailTemplatesApi` | merged into `EmailApi` (e.g. `viewMasterEmailTemplates`) |
| `UserEmailTemplatesApi` | merged into `EmailApi` (e.g. `createEmailTemplate`) |
| `ContactApi` | `ContactsApi` |
| `ContactListApi` | `ListsApi` |
| `DetectAddressApi` | **removed** — no v2 equivalent |
| `PostReturnAddressApi` | merged into `AddressesApi` (e.g. `createReturnAddress`) |
| `PostLetterApi` | **removed** — Letters is not part of v2 |
| `PostPostcardApi` | **removed** — Postcards is not part of v2 |
| `CountriesApi` | merged into `InternationalMessagingApi` (e.g. `listCountries`, `viewCountries`) |
| `TimezonesApi` | merged into `InternationalMessagingApi` (`timezones`) |
| `GlobalSendingApi` | merged into `InternationalMessagingApi` (`getCountriesForGlobalSending`, `selectCountriesForGlobalSending`) |
| `NumberApi` | `NumbersApi` (1:1: `numbersGet` → `viewYourNumbers`, `numbersSearchByCountryGet` → `viewAvailableNumbers`, `numbersBuyByDedicatedNumberPost` → `purchaseDedicatedNumber`), plus a brand-new `registerNumbers` method. `OwnNumbersApi` is a **separate new class** (Bring Your Own Number), *not* a split-off of `NumberApi`. |
| `AccountApi` | **split** into `ManagementApi` (`accountGet` → `viewAccountDetails`, `accountUseageBySubaccountGet` → `viewAccountUsage`) and `VerificationApi` (`forgotPasswordPut` → `forgotPassword`, `forgotUsernamePut` → `forgotUsername`). Four `AccountApi` methods have no v2 equivalent — see §8. |
| `AccountRechargeApi` | `TransactionsApi` (`purchaseRechargePackage`, `viewRechargePackages`, `currentPaymentInfo`, `updatePaymentInfo`) |
| `SubaccountApi` | `SubaccountsApi` |
| `ReferralAccountApi` | `ReferralsApi` |
| `ResellerAccountApi` | `ResellerApi` |
| `TransferCreditApi` | `ResellerApi` (`resellerTransferCredit`) |
| `SearchApi` | merged into `ListsApi` — `searchContactsListsGet` (`GET /search/contacts-lists`) → `viewContactLists` |
| `UploadApi` | `UploadsApi` |
| `SmsCampaignApi` | `SmsCampaignsApi` |
| `StatisticsApi` | `StatisticsApi` (unchanged) |
| `EmailToSmsApi` | `EmailToSmsApi` (unchanged) |
| `DeliveryIssuesApi` | renamed to `MessageDeliveryApi` (`createDeliveryIssue`, `getAllDeliveryIssues`) |
| — | **Genuinely new classes** (no v1 predecessor): `AlphaTagsApi`, `DefaultSendersApi`, `OwnNumbersApi` (Bring Your Own Number), `UrlShorteningApi`. Note `VerificationApi` and `MessageDeliveryApi` are *not* new — they are the split-off / renamed halves of `AccountApi` and `DeliveryIssuesApi` (see rows above). |

> **Dropped feature areas:** **Fax**, **Letters**, and **Postcards** have no
> presence in v2 — there is no `FaxApi` / `LettersApi` / `PostcardsApi` class
> and no fax/letter/postcard models, so there is no `sendFax` / `sendLetter`
> / `sendPostcard` equivalent. `DetectAddressApi` was dropped too. If your
> integration sends faxes, letters, or postcards, there is no v2 SDK path for
> it — call the REST API directly or keep the v1 SDK installed for those
> channels. (`PostReturnAddressApi` did survive, as `AddressesApi`.)

> **⚠️ The Voice naming trap — read this before touching voice code.** The two
> legacy voice classes effectively *swap names* in v2:
>
> - Legacy **`VoiceApi`** (send a voice message, view/export history, calculate
>   price, list languages, view receipts, cancel) → new **`VoiceMessagingApi`**.
> - Legacy **`VoiceDeliveryReceiptRulesApi`** (create/update/delete/view
>   delivery-receipt rules) → new **`VoiceApi`**.
>
> A blind find/replace of `VoiceApi` compiles fine but silently points
> voice-sending code at the delivery-receipt-rules class. To send voice
> messages in v2, use
> `ClickSend\Api\VoiceMessagingApi::sendVoiceMessage('application/json', $sendVoiceMessageRequest)`,
> **not** `VoiceApi`.

**Action required:** don't guess method names — for every call site, open the relevant `lib/Api/*.php` in this repo (or the generated `docs/Api/*.md`) and confirm the new method name and its parameter list. The rename isn't a mechanical find/replace; several old single-purpose classes were absorbed into a bigger class with differently-named methods.

## 4. Method signature changes

Legacy (v1) style:

```php
$apiInstance = new ClickSend\Api\SMSApi(new GuzzleHttp\Client(), $config);
$result = $apiInstance->smsSendPost($smsMessageCollection);
```

New (v2) style:

```php
$apiInstance = new ClickSend\Api\SmsApi(new GuzzleHttp\Client(), $config);
$result = $apiInstance->sendSms(contentType: 'application/json', sendSmsRequest: $sendSmsRequest);
```

Key differences per operation:

- **Request bodies are now typed per-operation models**, not shared collection classes. E.g. sending SMS now takes a `SendSmsRequest` (containing a `messages` array of `SendSmsRequestMessagesInner`), not the old `SmsMessageCollection`.
- Every operation gained a **`$content_type` parameter** (defaults come from a per-method `contentTypes` map, e.g. `SmsApi::contentTypes['sendSms'][0]`), to support content negotiation.
- Every operation now has **five generated variants** instead of four:
  - `operationName()` — synchronous, returns the parsed model
  - `operationNameWithHttpInfo()` — synchronous, returns status/headers/body
  - `operationNameAsync()` — returns a Guzzle promise
  - `operationNameAsyncWithHttpInfo()`
  - `operationNameRequest()` — **new**: returns the raw unsent PSR-7 `Request` object, for when you want to inspect/modify the request before sending it yourself
- `ApiException`, `getConfig()`, and the overall try/catch pattern are unchanged.
- New: `setHostIndex()` / `getHostIndex()` on every API class (multi-server support scaffold; not currently meaningful for ClickSend's single host).

## 5. Model changes

- Internal (de)serialization metadata properties were renamed: `$swaggerTypes` → `$openAPITypes`, `$swaggerFormats` → `$openAPIFormats`, `$swaggerModelName` → `$openAPIModelName`. This only matters if you were introspecting these protected statics directly (uncommon) — getters/setters (`getPhoneNumber()`, `setPhoneNumber()`, etc.) work the same way.
- Models now implement `\JsonSerializable` in addition to `ArrayAccess` — `json_encode($model)` now works directly.
- Response models (e.g. `Contact`) now include server-populated fields that used to be absent or mixed into the same class as the create payload (e.g. `contact_id`, `date_added`, `date_updated`). Split your code so **create/update requests use the narrower `*Request`/`CreateNewContact`-style model**, and **reads use the full resource model**.
- `const DISCRIMINATOR` still exists but now defaults to `null` on most models instead of a fixed string — only relevant if you relied on polymorphic discriminator behavior.

## 6. File uploads / multipart

The new SDK adds `lib/FormDataProcessor.php`, a dedicated helper for building multipart form-data bodies (used internally by upload-related operations, e.g. `UploadsApi`). There's no old-SDK equivalent to migrate from — this is purely additive; you don't need to change calling code, but if you were manually constructing multipart requests around the old `UploadApi`, you can likely delete that workaround now.

## 7. Docs and tests

- `docs/Api/*.md` and `docs/Model/*.md` are regenerated and now number 409 files (26 API + 383 model, up from 84), matching the new method/model surface — use these as the source of truth for exact new signatures rather than this table.
- `test/Api/*Test.php` and `test/Model/*Test.php` are also regenerated to match; if you had custom tests against the old SDK's classes, they'll need to be rewritten against the new class/method names.

## 8. Removed methods and dropped parameters

Beyond the dropped Fax / Letters / Postcards / DetectAddress classes (see §3), these individual legacy operations have **no equivalent anywhere in v2** (verified against all 26 v2 API classes). Check the current [ClickSend API reference](https://developers.clicksend.com/docs/rest/v3/) before upgrading if you rely on any of them:

| Legacy call | Was |
|---|---|
| `AccountApi::accountPost` | update account details |
| `AccountApi::accountVerifySendPut` | send account verification email |
| `AccountApi::accountVerifyVerifyByActivationTokenPut` | verify account by activation token |
| `AccountApi::forgotPasswordVerifyPut` | verify a forgotten-password token (`forgotPasswordPut` / `forgotUsernamePut` themselves survive on `VerificationApi`) |
| `MMSApi::mmsReceiptsGet` | view MMS delivery receipts |
| `MMSApi::mmsReceiptsReadPut` | mark MMS receipts as read |
| `VoiceApi::voiceReceiptsPost` | create a test voice receipt |
| `VoiceApi::voiceReceiptsReadPut` | mark voice receipts as read |

**Pagination parameters were dropped from several surviving methods.** `ContactListApi::listsGet($page, $limit)` → `ListsApi::viewLists()` takes no `page`/`limit`; the same applies to `ListsApi::viewListContacts()` (was `ContactApi::listsContactsByListIdGet($listId, $page, $limit, $updatedAfter)`) and `SubaccountsApi::viewSubaccounts()`. If a workflow depended on paging through these, confirm how the current API exposes pagination before shipping.

### Brand-new methods worth knowing about

- `NumbersApi::registerNumbers` — number registration.
- `SmsApi::viewASpecificInboundSmsMessage`, `SmsApi::viewASpecificSmsTemplate` — fetch a single inbound message / template by ID (v1 only exposed list endpoints).
- `OwnNumbersApi` — full Bring Your Own Number lifecycle (`listOwnNumbers`, `getOwnNumberDetail`, `updateOwnNumber`, `deleteOwnNumber`, `requestOwnNumberVerificationOtp`, `verifyOwnNumberOtp`).
- `AlphaTagsApi`, `DefaultSendersApi`, `UrlShorteningApi` — see §3.

## Suggested migration steps

1. Upgrade the project to PHP 8.1+ and update `composer.json` constraints (`guzzlehttp/psr7` is now required too).
2. Grep your codebase for `ClickSend\Api\` and `ClickSend\Model\` usages to inventory every call site.
3. If you override `Configuration::setHost()`, strip any trailing `/v3` (see §2).
4. For each call site, find the equivalent operation in the new SDK using the class mapping table above and the generated `docs/Api/*.md`, and confirm the new method name + request model. **Handle `VoiceApi` deliberately** — it is not the same class in v2 (see the Voice naming trap in §3).
5. Replace shared "collection" request objects with the specific `*Request` model for that operation, and add the leading `contentType` argument.
6. Check §8 for any removed methods or dropped pagination parameters your integration depends on before shipping.
7. Update exception handling only if you were inspecting model-specific fields on caught exceptions — `ApiException` itself is unchanged.
8. Run your test suite; regenerate/rewrite any tests that instantiated old SDK classes directly.
