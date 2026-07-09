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
$smsMessageCollection = new ClickSend\Model\SmsMessageCollection([
    'messages' => [
        ['source' => 'sdk', 'body' => 'Hello from ClickSend!', 'to' => '+61411111111'],
    ],
]);

try {
    $result = $apiInstance->smsSendPost($smsMessageCollection);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->smsSendPost: ', $e->getMessage(), PHP_EOL;
}
```

## Authentication

The API uses HTTP Basic authentication — your ClickSend **username** and **API key** (available from the [ClickSend Dashboard](https://dashboard.clicksend.com/#/account/subaccount)).

## Documentation

Full API reference: https://developers.clicksend.com/docs/rest/v3/

## Support

Need help? Contact [ClickSend Support](https://clicksend.com/contact) or visit the [Help Centre](https://help.clicksend.com/).
