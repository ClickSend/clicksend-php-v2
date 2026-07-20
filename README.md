# ClickSend PHP SDK

Official PHP client for the [ClickSend API](https://developers.clicksend.com/) — send and manage SMS, MMS, email, voice, fax, letters, postcards, and more.

## Requirements

PHP 8.1 and later.

## Installation

Via [Composer](https://getcomposer.org/):

```sh
composer require clicksend/clicksend-php
```

## Getting Started

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
    $result = $mmsApi->sendMms(null, $sendMmsRequest);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsApi->sendMms: ', $e->getMessage(), PHP_EOL;
}
```

## Authentication

The API uses HTTP Basic authentication — your ClickSend **username** and **API key** (available from the [ClickSend Dashboard](https://dashboard.clicksend.com/#/account/subaccount)).

## Documentation

Full API reference: https://developers.clicksend.com/docs/rest/v3/

## Support

Need help? Contact [ClickSend Support](https://clicksend.com/contact) or visit the [Help Centre](https://help.clicksend.com/).