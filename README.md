# ClickSend PHP SDK

[![Packagist Version](https://img.shields.io/packagist/v/clicksend/clicksend-php.svg)](https://packagist.org/packages/clicksend/clicksend-php)
[![Packagist Downloads](https://img.shields.io/packagist/dt/clicksend/clicksend-php.svg)](https://packagist.org/packages/clicksend/clicksend-php)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![API: v3](https://img.shields.io/badge/ClickSend%20API-v3-brightgreen.svg)](https://developers.clicksend.com/docs/rest/v3/)

Official PHP client for the [ClickSend API](https://developers.clicksend.com/) — send SMS, MMS, voice and email messages, run SMS and MMS campaigns, manage numbers, contacts and subaccounts, and pull delivery receipts and reporting through a single authenticated HTTPS client.

This library is generated from ClickSend's official OpenAPI v3 specification and is maintained by ClickSend. It covers every endpoint of the [ClickSend REST API](https://developers.clicksend.com/docs/rest/v3/).

- 📚 **API reference:** https://developers.clicksend.com/docs/rest/v3/
- 🔑 **Dashboard & API credentials:** https://dashboard.clicksend.com
- 🗂 **Source & issues:** https://github.com/ClickSend/clicksend-php-v2
- 💬 **Support:** https://help.clicksend.com

## Features

- **Messaging** — SMS, MMS, voice / text-to-speech, transactional email, email-to-SMS
- **Campaigns** — SMS and MMS campaigns
- **Numbers & sender IDs** — dedicated numbers, own numbers, alpha tags, default senders
- **Contacts** — contact lists, contacts and the address book
- **Account & billing** — account details, transactions, subaccounts, referrals, reseller accounts
- **Delivery & reporting** — delivery receipts, inbound messages, statistics
- **Extras** — URL shortening, file uploads, number verification, international messaging
- **Typed models** for every request and response, PSR-4 autoloaded
- **HTTP Basic auth** with your ClickSend username and API key
- **Identifiable traffic** — requests are sent with a `ClickSend-SDK/<version>/php` `User-Agent` by default
- MIT licensed

## Requirements

- PHP 8.1 or newer
- ext-curl, ext-json, ext-mbstring

## Installation

Via [Composer](https://getcomposer.org/):

```sh
composer require clicksend/clicksend-php
```

## Authentication

Every API class authenticates with HTTP Basic auth using your ClickSend **username** and **API key**, both available from the [ClickSend Dashboard](https://dashboard.clicksend.com/#/account/subaccount). Supply them through environment variables rather than hard-coding them:

```sh
export CLICKSEND_USERNAME="your-username"
export CLICKSEND_API_KEY="your-api-key"
```

## Quickstart

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$config = ClickSend\Configuration::getDefaultConfiguration()
    ->setUsername(getenv('CLICKSEND_USERNAME'))
    ->setPassword(getenv('CLICKSEND_API_KEY'));

$apiInstance = new ClickSend\Api\SmsApi(new GuzzleHttp\Client(), $config);
$sendSmsRequest = new ClickSend\Model\SendSmsRequest([
    'messages' => [
        ['source' => 'sdk', 'body' => 'Hello from ClickSend!', 'to' => '+61411111111'],
    ],
]);

try {
    // The first argument is the optional content type — pass `null` to use the default.
    // The request body is the second argument.
    $result = $apiInstance->sendSms(null, $sendSmsRequest);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->sendSms: ', $e->getMessage(), PHP_EOL;
}
```

## More Examples

### View account details

```php
$managementApi = new ClickSend\Api\ManagementApi(new GuzzleHttp\Client(), $config);

try {
    $account = $managementApi->viewAccountDetails();
    print_r($account);
} catch (Exception $e) {
    echo 'Exception when calling ManagementApi->viewAccountDetails: ', $e->getMessage(), PHP_EOL;
}
```

### Send an MMS

```php
$mmsApi = new ClickSend\Api\MmsApi(new GuzzleHttp\Client(), $config);
$sendMmsRequest = new ClickSend\Model\SendMmsRequest([
    'media_file' => 'https://clicksend.com/logo.png',
    'messages' => [
        ['to' => '+61411111111', 'from' => 'sdk', 'subject' => 'Hello', 'body' => 'Hello from ClickSend!', 'source' => 'sdk'],
    ],
]);

try {
    // As with sendSms, the first argument is the optional content type — pass `null`.
    $result = $mmsApi->sendMms(null, $sendMmsRequest);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsApi->sendMms: ', $e->getMessage(), PHP_EOL;
}
```

## Configuration

```php
$config = ClickSend\Configuration::getDefaultConfiguration()
    ->setUsername(getenv('CLICKSEND_USERNAME'))
    ->setPassword(getenv('CLICKSEND_API_KEY'))
    // Override the API base URL (default: https://rest.clicksend.com).
    ->setHost('https://rest.clicksend.com');

// Pass Guzzle options (timeouts, proxy, retries) when constructing the HTTP client.
$client = new GuzzleHttp\Client(['timeout' => 30]);
$apiInstance = new ClickSend\Api\SmsApi($client, $config);
```

## Error Handling

Non-2xx responses throw `ClickSend\ApiException`:

```php
try {
    $result = $apiInstance->sendSms(null, $sendSmsRequest);
} catch (ClickSend\ApiException $e) {
    $e->getCode();            // HTTP status code
    $e->getResponseBody();    // raw error payload from the API
    $e->getResponseHeaders(); // response headers
}
```

## Documentation

- Full REST API reference: https://developers.clicksend.com/docs/rest/v3/
- Per-endpoint SDK docs: the [`docs/`](docs) directory in this repository
- Source code: https://github.com/ClickSend/clicksend-php-v2

## Versioning

This package follows [semantic versioning](https://semver.org/). Breaking changes are released as major versions.

## Support

- Help Centre: https://help.clicksend.com
- Contact support: https://clicksend.com/contact
- SDK bugs and feature requests: https://github.com/ClickSend/clicksend-php-v2/issues

## License

Released under the [MIT License](https://opensource.org/licenses/MIT).

---

**Keywords:** clicksend, sms, sms api, send sms, bulk sms, text message, texting, mms, mms api, voice, voice call, text to speech, tts, ivr, email to sms, sms campaign, mms campaign, url shortening, number verification, messaging, notifications, otp, 2fa, two factor authentication, transactional sms, marketing sms, appointment reminders, alerts, php, php8, guzzle, rest api, clicksend sdk
