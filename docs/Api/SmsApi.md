# ClickSend\SmsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculateSmsPrice()**](SmsApi.md#calculateSmsPrice) | **POST** /v3/sms/price | Calculate SMS Price |
| [**cancelAllSms()**](SmsApi.md#cancelAllSms) | **PUT** /v3/sms/cancel-all | Cancel All SMS |
| [**cancelSms()**](SmsApi.md#cancelSms) | **PUT** /v3/sms/{message_id}/cancel | Cancel SMS |
| [**createSmsDeliveryReceiptRule()**](SmsApi.md#createSmsDeliveryReceiptRule) | **POST** /v3/automations/sms/receipts | Create SMS Delivery Receipt Rule |
| [**createSmsInboundAutomation()**](SmsApi.md#createSmsInboundAutomation) | **POST** /v3/automations/sms/inbound | Create SMS Inbound Automation |
| [**createSmsTemplate()**](SmsApi.md#createSmsTemplate) | **POST** /v3/sms/templates | Create SMS Template |
| [**createTestInboundSms()**](SmsApi.md#createTestInboundSms) | **POST** /v3/sms/inbound | Create Test Inbound SMS |
| [**createTestSmsReceipt()**](SmsApi.md#createTestSmsReceipt) | **POST** /v3/sms/receipts | Create Test SMS Receipt |
| [**deleteSmsDeliveryReceiptRule()**](SmsApi.md#deleteSmsDeliveryReceiptRule) | **DELETE** /v3/automations/sms/receipts/{receipt_rule_id} | Delete SMS Delivery Receipt Rule |
| [**deleteSmsInboundAutomation()**](SmsApi.md#deleteSmsInboundAutomation) | **DELETE** /v3/automations/sms/inbound/{inbound_rule_id} | Delete SMS Inbound Automation |
| [**deleteSmsTemplate()**](SmsApi.md#deleteSmsTemplate) | **DELETE** /v3/sms/templates/{template_id} | Delete SMS Template |
| [**exportSmsHistory()**](SmsApi.md#exportSmsHistory) | **GET** /v3/sms/history/export | Export SMS History |
| [**markInboundSmsAsRead()**](SmsApi.md#markInboundSmsAsRead) | **PUT** /v3/sms/inbound-read | Mark Inbound SMS as Read |
| [**markSmsReceiptAsRead()**](SmsApi.md#markSmsReceiptAsRead) | **PUT** /v3/sms/receipts-read | Mark SMS Receipt As Read |
| [**markSpecificInboundSmsMessageAsRead()**](SmsApi.md#markSpecificInboundSmsMessageAsRead) | **PUT** /v3/sms/inbound-read/{message_id} | Mark Specific Inbound SMS Message As Read |
| [**sendSms()**](SmsApi.md#sendSms) | **POST** /v3/sms/send | Send SMS |
| [**updateSmsDeliveryReceiptRule()**](SmsApi.md#updateSmsDeliveryReceiptRule) | **PUT** /v3/automations/sms/receipts/{receipt_rule_id} | Update SMS Delivery Receipt Rule |
| [**updateSmsInboundAutomation()**](SmsApi.md#updateSmsInboundAutomation) | **PUT** /v3/automations/sms/inbound/{inbound_rule_id} | Update SMS Inbound Automation |
| [**updateSmsTemplate()**](SmsApi.md#updateSmsTemplate) | **PUT** /v3/sms/templates/{template_id} | Update SMS Template |
| [**viewASpecificInboundSmsMessage()**](SmsApi.md#viewASpecificInboundSmsMessage) | **GET** /v3/sms/inbound/{original_message_id} | View a specific inbound SMS message |
| [**viewASpecificSmsTemplate()**](SmsApi.md#viewASpecificSmsTemplate) | **GET** /v3/sms/templates/{template_id} | View a Specific SMS Template |
| [**viewInboundSms()**](SmsApi.md#viewInboundSms) | **GET** /v3/sms/inbound | View Inbound SMS |
| [**viewSmsDeliveryReceiptRule()**](SmsApi.md#viewSmsDeliveryReceiptRule) | **GET** /v3/automations/sms/receipts/{receipt_rule_id} | View SMS Delivery Receipt Rule |
| [**viewSmsDeliveryReceiptRules()**](SmsApi.md#viewSmsDeliveryReceiptRules) | **GET** /v3/automations/sms/receipts | View SMS Delivery Receipt Rules |
| [**viewSmsHistory()**](SmsApi.md#viewSmsHistory) | **GET** /v3/sms/history | View SMS History |
| [**viewSmsInboundAutomation()**](SmsApi.md#viewSmsInboundAutomation) | **GET** /v3/automations/sms/inbound/{inbound_rule_id} | View SMS Inbound Automation |
| [**viewSmsInboundAutomations()**](SmsApi.md#viewSmsInboundAutomations) | **GET** /v3/automations/sms/inbound | View SMS Inbound Automations |
| [**viewSmsReceipts()**](SmsApi.md#viewSmsReceipts) | **GET** /v3/sms/receipts | View SMS Receipts |
| [**viewSmsTemplates()**](SmsApi.md#viewSmsTemplates) | **GET** /v3/sms/templates | View SMS Templates |
| [**viewSpecificSmsReceipt()**](SmsApi.md#viewSpecificSmsReceipt) | **GET** /v3/sms/receipts/{message_id} | View Specific SMS Receipt |


## `calculateSmsPrice()`

```php
calculateSmsPrice($content_type, $calculate_sms_price_request): \ClickSend\Model\CalculateSmsPrice
```

Calculate SMS Price

Use this endpoint to calculate the price of sending messages. The cost of sending messages varies based on the <a href=\"https://help.clicksend.com/article/h474eseq3a-how-many-characters-can-i-send-in-an-sms\" target=\"_blank\">type</a> and length of the message.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$calculate_sms_price_request = {"messages":[{"source":"php","body":"Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.","to":"+61411111111"},{"source":"php","body":"Chocolate bar icing icing oat cake carrot cake jelly cotton MWEvciEPIr.","to":"+61422222222"}]}; // \ClickSend\Model\CalculateSmsPriceRequest

try {
    $result = $apiInstance->calculateSmsPrice($content_type, $calculate_sms_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->calculateSmsPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **calculate_sms_price_request** | [**\ClickSend\Model\CalculateSmsPriceRequest**](../Model/CalculateSmsPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateSmsPrice**](../Model/CalculateSmsPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelAllSms()`

```php
cancelAllSms($content_type, $cancel_all_sms_request): \ClickSend\Model\CancelAllSms
```

Cancel All SMS

Use this endpoint to cancel all scheduled SMS. To cancel only one scheduled SMS, use the **Cancel SMS** endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$cancel_all_sms_request = new \ClickSend\Model\CancelAllSmsRequest(); // \ClickSend\Model\CancelAllSmsRequest

try {
    $result = $apiInstance->cancelAllSms($content_type, $cancel_all_sms_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->cancelAllSms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **cancel_all_sms_request** | [**\ClickSend\Model\CancelAllSmsRequest**](../Model/CancelAllSmsRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CancelAllSms**](../Model/CancelAllSms.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelSms()`

```php
cancelSms($message_id, $content_type): \ClickSend\Model\CancelSms
```

Cancel SMS

Use this endpoint to cancel a specific scheduled SMS. Unlike the **Cancel All SMS** endpoint, which cancels all scheduled SMS, this endpoint only cancels one specified scheduled SMS.  Specify the scheduled SMS to cancel by providing its _message_id_.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$message_id = 'message_id_example'; // string | The _message_id_ of the scheduled SMS to cancel.
$content_type = application/json; // string

try {
    $result = $apiInstance->cancelSms($message_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->cancelSms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**| The _message_id_ of the scheduled SMS to cancel. | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\CancelSms**](../Model/CancelSms.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createSmsDeliveryReceiptRule()`

```php
createSmsDeliveryReceiptRule($content_type, $create_sms_delivery_receipt_rule_request): \ClickSend\Model\CreateSmsDeliveryReceiptRule
```

Create SMS Delivery Receipt Rule

_Create sms delivery receipt automations_  Create sms delivery receipt automations  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_sms_delivery_receipt_rule_request = new \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->createSmsDeliveryReceiptRule($content_type, $create_sms_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->createSmsDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_sms_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest**](../Model/CreateSmsDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateSmsDeliveryReceiptRule**](../Model/CreateSmsDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createSmsInboundAutomation()`

```php
createSmsInboundAutomation($content_type, $create_sms_inbound_automation_request): \ClickSend\Model\CreateSmsInboundAutomation
```

Create SMS Inbound Automation

_Create new inbound sms automation_  Create new inbound sms automation  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | dedicated_number | string | true | none | Decicated Number. Can be '\\*' to apply to all numbers. | | rule_name | string | true | none | Rule Name. | | message_search_type | number | true | none | Message Search Type: 0=Any message, 1=starts with, 2=contains, 3=does not contain. | | message_search_term | string | true | none | Message search term. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. | | webhook_type | string | false | Required when action = URL only | Set as post, get, or json to change the format of the request sent. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_sms_inbound_automation_request = new \ClickSend\Model\CreateSmsInboundAutomationRequest(); // \ClickSend\Model\CreateSmsInboundAutomationRequest

try {
    $result = $apiInstance->createSmsInboundAutomation($content_type, $create_sms_inbound_automation_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->createSmsInboundAutomation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_sms_inbound_automation_request** | [**\ClickSend\Model\CreateSmsInboundAutomationRequest**](../Model/CreateSmsInboundAutomationRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateSmsInboundAutomation**](../Model/CreateSmsInboundAutomation.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createSmsTemplate()`

```php
createSmsTemplate($content_type, $create_sms_template_request): \ClickSend\Model\CreateSmsTemplate
```

Create SMS Template

Use this endpoint to create a SMS template that you can use for sending SMS.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_sms_template_request = new \ClickSend\Model\CreateSmsTemplateRequest(); // \ClickSend\Model\CreateSmsTemplateRequest

try {
    $result = $apiInstance->createSmsTemplate($content_type, $create_sms_template_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->createSmsTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_sms_template_request** | [**\ClickSend\Model\CreateSmsTemplateRequest**](../Model/CreateSmsTemplateRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateSmsTemplate**](../Model/CreateSmsTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createTestInboundSms()`

```php
createTestInboundSms($content_type, $create_test_inbound_sms_request): \ClickSend\Model\CreateTestInboundSms
```

Create Test Inbound SMS

Use this endpoint to generate and send a test <a href=\"https://help.clicksend.com/article/ik4hw5xu35-can-i-receive-inbound-sms-to-my-url\" target=\"_blank\">inbound SMS</a> to your webhook URL. Inbound SMS are messages sent by your recipient to you.  This test endpoint allows you to verify that the inbound SMS is correctly sent to your webhook URL.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_test_inbound_sms_request = new \ClickSend\Model\CreateTestInboundSmsRequest(); // \ClickSend\Model\CreateTestInboundSmsRequest

try {
    $result = $apiInstance->createTestInboundSms($content_type, $create_test_inbound_sms_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->createTestInboundSms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_test_inbound_sms_request** | [**\ClickSend\Model\CreateTestInboundSmsRequest**](../Model/CreateTestInboundSmsRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateTestInboundSms**](../Model/CreateTestInboundSms.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createTestSmsReceipt()`

```php
createTestSmsReceipt($content_type, $create_test_sms_receipt_request): \ClickSend\Model\CreateTestSmsReceipt
```

Create Test SMS Receipt

Use this endpoint to generate and send a test <a href=\"https://help.clicksend.com/article/49eq1qdcui-how-do-i-receive-sms-delivery-receipts-delivery-status-updates\" target=\"_blank\">SMS delivery receipt</a> to your webhook URL. When you send an SMS, a delivery receipt is generated and can be received at your webhook URL. This test endpoint allows you to verify that the receipt is correctly sent to your webhook URL.  Additionally, you can obtain SMS receipts by setting the webhook URL to **poll** and periodically calling the **View SMS Receipt** endpoint to check for new receipts. This process is known as _polling_.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_test_sms_receipt_request = new \ClickSend\Model\CreateTestSmsReceiptRequest(); // \ClickSend\Model\CreateTestSmsReceiptRequest

try {
    $result = $apiInstance->createTestSmsReceipt($content_type, $create_test_sms_receipt_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->createTestSmsReceipt: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_test_sms_receipt_request** | [**\ClickSend\Model\CreateTestSmsReceiptRequest**](../Model/CreateTestSmsReceiptRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateTestSmsReceipt**](../Model/CreateTestSmsReceipt.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSmsDeliveryReceiptRule()`

```php
deleteSmsDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\DeleteSmsDeliveryReceiptRule
```

Delete SMS Delivery Receipt Rule

_Delete sms delivery receipt automation_  Delete sms delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteSmsDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->deleteSmsDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteSmsDeliveryReceiptRule**](../Model/DeleteSmsDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSmsInboundAutomation()`

```php
deleteSmsInboundAutomation($inbound_rule_id, $content_type): \ClickSend\Model\DeleteSmsInboundAutomation
```

Delete SMS Inbound Automation

_Delete inbound sms automation_  Delete inbound sms automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | inbound_rule_id | path | integer(int32) | true | Inbound rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$inbound_rule_id = 'inbound_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteSmsInboundAutomation($inbound_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->deleteSmsInboundAutomation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **inbound_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteSmsInboundAutomation**](../Model/DeleteSmsInboundAutomation.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSmsTemplate()`

```php
deleteSmsTemplate($template_id, $content_type): \ClickSend\Model\DeleteSmsTemplate
```

Delete SMS Template

Use this endpoint to delete a <a href=\"https://help.clicksend.com/article/9z9uloaz8y-sms-templates-for-different-industries\" target=\"_blank\">SMS template</a>. Specify the SMS template to delete by providing its _template_id_.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string | The ID of the template to delete.
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteSmsTemplate($template_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->deleteSmsTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**| The ID of the template to delete. | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteSmsTemplate**](../Model/DeleteSmsTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportSmsHistory()`

```php
exportSmsHistory($content_type, $filename, $page, $limit, $q, $order_by, $date_from, $date_to): \ClickSend\Model\ExportSmsHistory
```

Export SMS History

Use this endpoint to create a download link of your SMS history. You can filter the SMS history result using the query parameters.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$filename = 'export.csv'; // string | The filename of the result. It should be in the .csv format.
$page = 1; // int | The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1.
$limit = 15; // int | The number of items to return per page. This parameter controls the size of each page of results. The default value is 15.
$q = 'field_name'; // string | Allows filtering of results based on your search criteria. The query should be in the format `field_name:value`.  1. **Field Name**: The field within the SMS history you want to filter by. You can use the following fields:          - _Status_: The status of the SMS. Available values for status are: Queued, Completed, Scheduled, WaitApproval, Failed, Cancelled, CancelledAfterReview, Received, Sent.              - _To_: The recipient of the SMS.              - _from_: The sender of the SMS.              - _subaccount_id_: The sub-account identifier.              - _message_id_: The ID of your SMS.          2. **Value**: The text or keyword you're searching for within the specified field. If left empty after the colon, the filter will look for all templates with any value in the **Field Name**.             For example, if you are searching for a SMS with the status of _Scheduled_, the final query would look like this:    `q=status:Scheduled`  <div class=\"info-box\">   <h4><i class=\"fas fa-info-circle\"></i> Note:</h4>   <div>   <p>Some characters have to be encoded. For example, if you are searching for SMS sent from the phone number +61437085284, your search query q would be:<br/></p>     <ul>       <li>q=from:%2B61437085284</li>     </ul>     <p>You can use the <a href=\"https://www.urlencoder.org/\" target=\"_blank\">URL encoder</a> to encode the text. If a character is not an alphanumeric character (A-Z, a-z, 0-9), it is typically either reserved or unsafe and should be encoded.</p>   </div> </div>
$order_by = 'date:asc'; // string | Specifies the field and order to sort the results by. The value is composed of the field name followed by a colon and the sort direction (asc for ascending or desc for descending).  The default sort order is by date in ascending order. You can use the following fields:    - _date_    - _username_   - _from_    - _to_   - _status_    - _body_  For example, if you want to order by the most recently sent SMS, you should sort by date in descending order. The query would look like this:    `order_by=date:desc`
$date_from = 56; // int | Start date to filter results. It should be in <a href=\"http://help.clicksend.com/what-is-a-unix-timestamp\" target=\"_blank\">Unix format</a>.
$date_to = 56; // int | End date to filter results. It should be in <a href=\"http://help.clicksend.com/what-is-a-unix-timestamp\" target=\"_blank\">Unix format</a>.

try {
    $result = $apiInstance->exportSmsHistory($content_type, $filename, $page, $limit, $q, $order_by, $date_from, $date_to);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->exportSmsHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **filename** | **string**| The filename of the result. It should be in the .csv format. | [optional] [default to &#39;export.csv&#39;] |
| **page** | **int**| The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1. | [optional] [default to 1] |
| **limit** | **int**| The number of items to return per page. This parameter controls the size of each page of results. The default value is 15. | [optional] [default to 15] |
| **q** | **string**| Allows filtering of results based on your search criteria. The query should be in the format &#x60;field_name:value&#x60;.  1. **Field Name**: The field within the SMS history you want to filter by. You can use the following fields:          - _Status_: The status of the SMS. Available values for status are: Queued, Completed, Scheduled, WaitApproval, Failed, Cancelled, CancelledAfterReview, Received, Sent.              - _To_: The recipient of the SMS.              - _from_: The sender of the SMS.              - _subaccount_id_: The sub-account identifier.              - _message_id_: The ID of your SMS.          2. **Value**: The text or keyword you&#39;re searching for within the specified field. If left empty after the colon, the filter will look for all templates with any value in the **Field Name**.             For example, if you are searching for a SMS with the status of _Scheduled_, the final query would look like this:    &#x60;q&#x3D;status:Scheduled&#x60;  &lt;div class&#x3D;\&quot;info-box\&quot;&gt;   &lt;h4&gt;&lt;i class&#x3D;\&quot;fas fa-info-circle\&quot;&gt;&lt;/i&gt; Note:&lt;/h4&gt;   &lt;div&gt;   &lt;p&gt;Some characters have to be encoded. For example, if you are searching for SMS sent from the phone number +61437085284, your search query q would be:&lt;br/&gt;&lt;/p&gt;     &lt;ul&gt;       &lt;li&gt;q&#x3D;from:%2B61437085284&lt;/li&gt;     &lt;/ul&gt;     &lt;p&gt;You can use the &lt;a href&#x3D;\&quot;https://www.urlencoder.org/\&quot; target&#x3D;\&quot;_blank\&quot;&gt;URL encoder&lt;/a&gt; to encode the text. If a character is not an alphanumeric character (A-Z, a-z, 0-9), it is typically either reserved or unsafe and should be encoded.&lt;/p&gt;   &lt;/div&gt; &lt;/div&gt; | [optional] [default to &#39;field_name&#39;] |
| **order_by** | **string**| Specifies the field and order to sort the results by. The value is composed of the field name followed by a colon and the sort direction (asc for ascending or desc for descending).  The default sort order is by date in ascending order. You can use the following fields:    - _date_    - _username_   - _from_    - _to_   - _status_    - _body_  For example, if you want to order by the most recently sent SMS, you should sort by date in descending order. The query would look like this:    &#x60;order_by&#x3D;date:desc&#x60; | [optional] [default to &#39;date:asc&#39;] |
| **date_from** | **int**| Start date to filter results. It should be in &lt;a href&#x3D;\&quot;http://help.clicksend.com/what-is-a-unix-timestamp\&quot; target&#x3D;\&quot;_blank\&quot;&gt;Unix format&lt;/a&gt;. | [optional] |
| **date_to** | **int**| End date to filter results. It should be in &lt;a href&#x3D;\&quot;http://help.clicksend.com/what-is-a-unix-timestamp\&quot; target&#x3D;\&quot;_blank\&quot;&gt;Unix format&lt;/a&gt;. | [optional] |

### Return type

[**\ClickSend\Model\ExportSmsHistory**](../Model/ExportSmsHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `markInboundSmsAsRead()`

```php
markInboundSmsAsRead($content_type, $mark_sms_receipt_as_read_request): \ClickSend\Model\MarkInboundSmsAsRead
```

Mark Inbound SMS as Read

Use this endpoint to mark all <a href=\"https://help.clicksend.com/article/ik4hw5xu35-can-i-receive-inbound-sms-to-my-url\" target=\"_blank\">inbound SMS</a> as read. Inbound SMS that has been marked as read won’t be shown in the **View Inbound SMS** endpoint. You can still use the **View Specific Inbound SMS** endpoint to view inbound SMS marked as read.  In the request, you can optionally add a _date_before_ parameter to only mark inbound SMS sent before that date as read.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$mark_sms_receipt_as_read_request = new \ClickSend\Model\MarkSmsReceiptAsReadRequest(); // \ClickSend\Model\MarkSmsReceiptAsReadRequest

try {
    $result = $apiInstance->markInboundSmsAsRead($content_type, $mark_sms_receipt_as_read_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->markInboundSmsAsRead: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **mark_sms_receipt_as_read_request** | [**\ClickSend\Model\MarkSmsReceiptAsReadRequest**](../Model/MarkSmsReceiptAsReadRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\MarkInboundSmsAsRead**](../Model/MarkInboundSmsAsRead.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `markSmsReceiptAsRead()`

```php
markSmsReceiptAsRead($content_type, $mark_sms_receipt_as_read_request): \ClickSend\Model\MarkSmsReceiptAsRead
```

Mark SMS Receipt As Read

Use this endpoint to mark all <a target=\"_blank\" href=\"https://help.clicksend.com/article/49eq1qdcui-how-do-i-receive-sms-delivery-receipts-delivery-status-updates\">SMS delivery receipts</a> as read. Delivery receipts that have been marked as read won’t be shown in the **View SMS Receipts** endpoint.  You can still use the **View Specific SMS Receipt** endpoint to view delivery receipts marked as read. In the request, you can optionally add a _date_before_ parameter to only mark receipts sent before that date as read

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$mark_sms_receipt_as_read_request = new \ClickSend\Model\MarkSmsReceiptAsReadRequest(); // \ClickSend\Model\MarkSmsReceiptAsReadRequest

try {
    $result = $apiInstance->markSmsReceiptAsRead($content_type, $mark_sms_receipt_as_read_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->markSmsReceiptAsRead: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **mark_sms_receipt_as_read_request** | [**\ClickSend\Model\MarkSmsReceiptAsReadRequest**](../Model/MarkSmsReceiptAsReadRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\MarkSmsReceiptAsRead**](../Model/MarkSmsReceiptAsRead.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `markSpecificInboundSmsMessageAsRead()`

```php
markSpecificInboundSmsMessageAsRead($message_id, $content_type): \ClickSend\Model\MarkSpecificInboundSmsMessageAsRead
```

Mark Specific Inbound SMS Message As Read

Use this endpoint to mark a specific <a href=\"https://help.clicksend.com/article/ik4hw5xu35-can-i-receive-inbound-sms-to-my-url\" target=\"_blank\">inbound SMS</a> as read. Unlike the **View Inbound SMS** endpoint, which marks all inbound SMS as read,  this endpoint only marks one specified inbound SMS. Specify the SMS to be marked as read by providing its _message_id_.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$message_id = 'message_id_example'; // string | The message_id of the inbound SMS to mark as read.  <div class=\"info-box\">   <h4><i class=\"fas fa-info-circle\"></i> Note:</h4>   <p>     When you receive an inbound message, you will get two parameters: <em>original_message_id</em> and <em>message_id</em>:   </p>   <ul>     <li><em>original_message_id</em>: This is the ID of the outbound message sent to the recipient</li>     <li><em>message_id</em>: This is the ID of the inbound message sent by the recipient.</li>   </ul> </div>
$content_type = application/json; // string

try {
    $result = $apiInstance->markSpecificInboundSmsMessageAsRead($message_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->markSpecificInboundSmsMessageAsRead: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**| The message_id of the inbound SMS to mark as read.  &lt;div class&#x3D;\&quot;info-box\&quot;&gt;   &lt;h4&gt;&lt;i class&#x3D;\&quot;fas fa-info-circle\&quot;&gt;&lt;/i&gt; Note:&lt;/h4&gt;   &lt;p&gt;     When you receive an inbound message, you will get two parameters: &lt;em&gt;original_message_id&lt;/em&gt; and &lt;em&gt;message_id&lt;/em&gt;:   &lt;/p&gt;   &lt;ul&gt;     &lt;li&gt;&lt;em&gt;original_message_id&lt;/em&gt;: This is the ID of the outbound message sent to the recipient&lt;/li&gt;     &lt;li&gt;&lt;em&gt;message_id&lt;/em&gt;: This is the ID of the inbound message sent by the recipient.&lt;/li&gt;   &lt;/ul&gt; &lt;/div&gt; | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\MarkSpecificInboundSmsMessageAsRead**](../Model/MarkSpecificInboundSmsMessageAsRead.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendSms()`

```php
sendSms($content_type, $send_sms_request): \ClickSend\Model\SendSms
```

Send SMS

Use this endpoint to send messages to your recipients, either as phone numbers or contacts from your contact list.  The sender of the message (<a href=\"https://help.clicksend.com/article/4kgj7krx00-what-is-a-sender-id-or-sender-number\" target=\"_blank\"><strong>Sender ID</strong></a>) can be a shared number, a dedicated number, alpha tag (business name), or your own number.  You can send messages both locally and globally, subject to the country restrictions. The cost of sending messages varies based on the <a href=\"https://help.clicksend.com/article/h474eseq3a-how-many-characters-can-i-send-in-an-sms\" target=\"_blank\">type</a> and length of the message.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_sms_request = {"messages":[{"source":"php","body":"Jelly liquorice marshmallow candy carrot cake 4Eyffjs1vL.","to":"+61411111111"},{"source":"php","body":"Chocolate bar icing icing oat cake carrot cake jelly cotton MWEvciEPIr.","to":"+61422222222"}]}; // \ClickSend\Model\SendSmsRequest

try {
    $result = $apiInstance->sendSms($content_type, $send_sms_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->sendSms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_sms_request** | [**\ClickSend\Model\SendSmsRequest**](../Model/SendSmsRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendSms**](../Model/SendSms.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateSmsDeliveryReceiptRule()`

```php
updateSmsDeliveryReceiptRule($receipt_rule_id, $content_type, $create_sms_delivery_receipt_rule_request): \ClickSend\Model\UpdateSmsDeliveryReceiptRule
```

Update SMS Delivery Receipt Rule

_Update sms delivery receipt automation_  Update sms delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string
$create_sms_delivery_receipt_rule_request = new \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->updateSmsDeliveryReceiptRule($receipt_rule_id, $content_type, $create_sms_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->updateSmsDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **create_sms_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest**](../Model/CreateSmsDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateSmsDeliveryReceiptRule**](../Model/UpdateSmsDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateSmsInboundAutomation()`

```php
updateSmsInboundAutomation($inbound_rule_id, $content_type, $update_sms_inbound_automation_request): \ClickSend\Model\UpdateSmsInboundAutomation
```

Update SMS Inbound Automation

_Update inbound sms automation_  Update inbound sms automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | inbound_rule_id | path | integer(int32) | true | Inbound rule id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | dedicated_number | string | true | none | Dedicated Number. Can be '\\*' to apply to all numbers. | | rule_name | string | true | none | Rule Name. | | message_search_type | number | true | none | Message Search Type: 0=Any message, 1=starts with, 2=contains, 3=does not contain. | | message_search_term | string | true | none | Message search term. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. | | webhook_type | string | false | Required when action = URL only | Set as post, get, or json to change the format of the request sent. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$inbound_rule_id = 'inbound_rule_id_example'; // string
$content_type = application/json; // string
$update_sms_inbound_automation_request = new \ClickSend\Model\UpdateSmsInboundAutomationRequest(); // \ClickSend\Model\UpdateSmsInboundAutomationRequest

try {
    $result = $apiInstance->updateSmsInboundAutomation($inbound_rule_id, $content_type, $update_sms_inbound_automation_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->updateSmsInboundAutomation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **inbound_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_sms_inbound_automation_request** | [**\ClickSend\Model\UpdateSmsInboundAutomationRequest**](../Model/UpdateSmsInboundAutomationRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateSmsInboundAutomation**](../Model/UpdateSmsInboundAutomation.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateSmsTemplate()`

```php
updateSmsTemplate($template_id, $content_type, $create_sms_template_request): \ClickSend\Model\UpdateSmsTemplate
```

Update SMS Template

Use this endpoint to update a <a href=\"https://help.clicksend.com/article/9z9uloaz8y-sms-templates-for-different-industries\" target=\"_blank\">SMS template</a>.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string | The ID of the template to update.
$content_type = application/json; // string
$create_sms_template_request = new \ClickSend\Model\CreateSmsTemplateRequest(); // \ClickSend\Model\CreateSmsTemplateRequest

try {
    $result = $apiInstance->updateSmsTemplate($template_id, $content_type, $create_sms_template_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->updateSmsTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**| The ID of the template to update. | |
| **content_type** | **string**|  | [optional] |
| **create_sms_template_request** | [**\ClickSend\Model\CreateSmsTemplateRequest**](../Model/CreateSmsTemplateRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateSmsTemplate**](../Model/UpdateSmsTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewASpecificInboundSmsMessage()`

```php
viewASpecificInboundSmsMessage($original_message_id, $content_type): \ClickSend\Model\ViewASpecificInboundSmsMessage
```

View a specific inbound SMS message

Use this endpoint to retrieve a specific inbound SMS, including those that have been marked as read.  Inbound SMS are messages sent by your recipient to you. This endpoint enables you to retrieve those inbound SMS.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$original_message_id = 'original_message_id_example'; // string | The _original_message_id_ of the inbound SMS to view. If the recipient replied with multiple messages, this endpoint returns the first inbound SMS received.  <div class=\"info-box\">   <h4><i class=\"fas fa-info-circle\"></i> Note:</h4>   <p>     When you receive an inbound message, you will get two parameters: <em>original_message_id</em> and <em>message_id</em>:   </p>   <ul>     <li><em>original_message_id</em>: This is the ID of the outbound message sent to the recipient</li>     <li><em>message_id</em>: This is the ID of the inbound message sent by the recipient.</li>   </ul> </div>
$content_type = application/json; // string

try {
    $result = $apiInstance->viewASpecificInboundSmsMessage($original_message_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewASpecificInboundSmsMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **original_message_id** | **string**| The _original_message_id_ of the inbound SMS to view. If the recipient replied with multiple messages, this endpoint returns the first inbound SMS received.  &lt;div class&#x3D;\&quot;info-box\&quot;&gt;   &lt;h4&gt;&lt;i class&#x3D;\&quot;fas fa-info-circle\&quot;&gt;&lt;/i&gt; Note:&lt;/h4&gt;   &lt;p&gt;     When you receive an inbound message, you will get two parameters: &lt;em&gt;original_message_id&lt;/em&gt; and &lt;em&gt;message_id&lt;/em&gt;:   &lt;/p&gt;   &lt;ul&gt;     &lt;li&gt;&lt;em&gt;original_message_id&lt;/em&gt;: This is the ID of the outbound message sent to the recipient&lt;/li&gt;     &lt;li&gt;&lt;em&gt;message_id&lt;/em&gt;: This is the ID of the inbound message sent by the recipient.&lt;/li&gt;   &lt;/ul&gt; &lt;/div&gt; | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewASpecificInboundSmsMessage**](../Model/ViewASpecificInboundSmsMessage.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewASpecificSmsTemplate()`

```php
viewASpecificSmsTemplate($template_id, $content_type): \ClickSend\Model\ViewASpecificSmsTemplate
```

View a Specific SMS Template

Use this endpoint to retrieve a <a href=\"https://help.clicksend.com/article/9z9uloaz8y-sms-templates-for-different-industries\" target=\"_blank\">SMS template</a>. Specify which template to retrieve using the template ID.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string | The ID of the template to retrieve
$content_type = application/json; // string

try {
    $result = $apiInstance->viewASpecificSmsTemplate($template_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewASpecificSmsTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**| The ID of the template to retrieve | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewASpecificSmsTemplate**](../Model/ViewASpecificSmsTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewInboundSms()`

```php
viewInboundSms($content_type, $page, $limit): \ClickSend\Model\ViewInboundSms
```

View Inbound SMS

Use this endpoint to retrieve <a href=\"https://help.clicksend.com/article/49eq1qdcui-how-do-i-receive-sms-delivery-receipts-delivery-status-updates\" target=\"_blank\">SMS delivery receipts</a> sent by your recipient.  To be able to view receipts, add a <a href=\"https://help.clicksend.com/article/ut4ttdrrai-incoming-reply-sms-options\">inbound rule</a> with the Action set to **POLL** in the Dashboard, or use the [**Create SMS Inbound Automation**](/automations/sms/other/create-sms-inbound-automation) endpoint.  Control [pagination](/#pagination) with the _page_ and _limit_ query parameters to specify the page of results and the number of items returned.  <div class=\"info-box\">   <h4><i class=\"fas fa-info-circle\"></i> Note:</h4>   <p>If you have multiple inbound rules set to <strong>POLL</strong>, you will receive the inbound message multiple times.</p> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$page = 1; // int | The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1.
$limit = 15; // int | The number of items to return per page. This parameter controls the size of each page of results. The default value is 15.

try {
    $result = $apiInstance->viewInboundSms($content_type, $page, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewInboundSms: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **page** | **int**| The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1. | [optional] [default to 1] |
| **limit** | **int**| The number of items to return per page. This parameter controls the size of each page of results. The default value is 15. | [optional] [default to 15] |

### Return type

[**\ClickSend\Model\ViewInboundSms**](../Model/ViewInboundSms.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsDeliveryReceiptRule()`

```php
viewSmsDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\ViewSmsDeliveryReceiptRule
```

View SMS Delivery Receipt Rule

_Get specific sms delivery receipt automation_  Get specific sms delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSmsDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSmsDeliveryReceiptRule**](../Model/ViewSmsDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsDeliveryReceiptRules()`

```php
viewSmsDeliveryReceiptRules($content_type): \ClickSend\Model\ViewSmsDeliveryReceiptRules
```

View SMS Delivery Receipt Rules

_Get all sms delivery receipt automations_  Get all sms delivery receipt automations  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSmsDeliveryReceiptRules($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsDeliveryReceiptRules: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSmsDeliveryReceiptRules**](../Model/ViewSmsDeliveryReceiptRules.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsHistory()`

```php
viewSmsHistory($content_type, $page, $limit, $q, $order_by, $date_from, $date_to): \ClickSend\Model\ViewSmsHistory
```

View SMS History

Use this endpoint to view previously sent SMS. You can filter the SMS history result using the query parameters.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$page = 1; // int | The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1.
$limit = 15; // int | The number of items to return per page. This parameter controls the size of each page of results. The default value is 15.
$q = 'field_name'; // string | Allows filtering of results based on your search criteria. The query should be in the format `field_name:value`.  1. **Field Name**: The field within the SMS history you want to filter by. You can use the following fields:          - _Status_: The status of the SMS. Available values for status are: Queued, Completed, Scheduled, WaitApproval, Failed, Cancelled, CancelledAfterReview, Received, Sent.              - _To_: The recipient of the SMS.              - _from_: The sender of the SMS.              - _subaccount_id_: The sub-account identifier.              - _message_id_: The ID of your SMS.          2. **Value**: The text or keyword you're searching for within the specified field. If left empty after the colon, the filter will look for all templates with any value in the **Field Name**.             For example, if you are searching for a SMS with the status of Scheduled, the final query would look like this:    `q=status:Scheduled`  <div class=\"info-box\">   <h4><i class=\"fas fa-info-circle\"></i> Note:</h4>   <div>    <p>Some characters have to be encoded. For example, if you are searching for SMS sent from the phone number +61437085284, your search query q would be:<br/></p>     <ul>       <li>q=from:%2B61437085284</li>     </ul>     <p>You can use the <a href=\"https://www.urlencoder.org/\" target=\"_blank\">URL encoder</a> to encode the text. If a character is not an alphanumeric character (A-Z, a-z, 0-9), it is typically either reserved or unsafe and should be encoded.</p>   </div> </div>
$order_by = 'date:asc'; // string | Specifies the field and order to sort the results by. The value is composed of the field name followed by a colon and the sort direction (_asc_ for ascending or _desc_ for descending).  The default sort order is by _date_ in ascending order. You can use the following fields:    - _date_   - _username_   - _from_    - _to_   - _status_   - _body_  For example, if you want to order by the most recently sent SMS, you should sort by date in descending order. The query would look like this:    `order_by=date:desc`
$date_from = 56; // int | Start date to filter results. It should be in <a href=\"http://help.clicksend.com/what-is-a-unix-timestamp\" target=\"_blank\">Unix format</a>.
$date_to = 56; // int | End date to filter results. It should be in <a href=\"http://help.clicksend.com/what-is-a-unix-timestamp\" target=\"_blank\">Unix format</a>.

try {
    $result = $apiInstance->viewSmsHistory($content_type, $page, $limit, $q, $order_by, $date_from, $date_to);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **page** | **int**| The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1. | [optional] [default to 1] |
| **limit** | **int**| The number of items to return per page. This parameter controls the size of each page of results. The default value is 15. | [optional] [default to 15] |
| **q** | **string**| Allows filtering of results based on your search criteria. The query should be in the format &#x60;field_name:value&#x60;.  1. **Field Name**: The field within the SMS history you want to filter by. You can use the following fields:          - _Status_: The status of the SMS. Available values for status are: Queued, Completed, Scheduled, WaitApproval, Failed, Cancelled, CancelledAfterReview, Received, Sent.              - _To_: The recipient of the SMS.              - _from_: The sender of the SMS.              - _subaccount_id_: The sub-account identifier.              - _message_id_: The ID of your SMS.          2. **Value**: The text or keyword you&#39;re searching for within the specified field. If left empty after the colon, the filter will look for all templates with any value in the **Field Name**.             For example, if you are searching for a SMS with the status of Scheduled, the final query would look like this:    &#x60;q&#x3D;status:Scheduled&#x60;  &lt;div class&#x3D;\&quot;info-box\&quot;&gt;   &lt;h4&gt;&lt;i class&#x3D;\&quot;fas fa-info-circle\&quot;&gt;&lt;/i&gt; Note:&lt;/h4&gt;   &lt;div&gt;    &lt;p&gt;Some characters have to be encoded. For example, if you are searching for SMS sent from the phone number +61437085284, your search query q would be:&lt;br/&gt;&lt;/p&gt;     &lt;ul&gt;       &lt;li&gt;q&#x3D;from:%2B61437085284&lt;/li&gt;     &lt;/ul&gt;     &lt;p&gt;You can use the &lt;a href&#x3D;\&quot;https://www.urlencoder.org/\&quot; target&#x3D;\&quot;_blank\&quot;&gt;URL encoder&lt;/a&gt; to encode the text. If a character is not an alphanumeric character (A-Z, a-z, 0-9), it is typically either reserved or unsafe and should be encoded.&lt;/p&gt;   &lt;/div&gt; &lt;/div&gt; | [optional] [default to &#39;field_name&#39;] |
| **order_by** | **string**| Specifies the field and order to sort the results by. The value is composed of the field name followed by a colon and the sort direction (_asc_ for ascending or _desc_ for descending).  The default sort order is by _date_ in ascending order. You can use the following fields:    - _date_   - _username_   - _from_    - _to_   - _status_   - _body_  For example, if you want to order by the most recently sent SMS, you should sort by date in descending order. The query would look like this:    &#x60;order_by&#x3D;date:desc&#x60; | [optional] [default to &#39;date:asc&#39;] |
| **date_from** | **int**| Start date to filter results. It should be in &lt;a href&#x3D;\&quot;http://help.clicksend.com/what-is-a-unix-timestamp\&quot; target&#x3D;\&quot;_blank\&quot;&gt;Unix format&lt;/a&gt;. | [optional] |
| **date_to** | **int**| End date to filter results. It should be in &lt;a href&#x3D;\&quot;http://help.clicksend.com/what-is-a-unix-timestamp\&quot; target&#x3D;\&quot;_blank\&quot;&gt;Unix format&lt;/a&gt;. | [optional] |

### Return type

[**\ClickSend\Model\ViewSmsHistory**](../Model/ViewSmsHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsInboundAutomation()`

```php
viewSmsInboundAutomation($inbound_rule_id, $content_type): \ClickSend\Model\ViewSmsInboundAutomation
```

View SMS Inbound Automation

_Get specific inbound sms automation_  Get specific inbound sms automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | inbound_rule_id | path | integer(int32) | true | Inbound rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$inbound_rule_id = 'inbound_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSmsInboundAutomation($inbound_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsInboundAutomation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **inbound_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSmsInboundAutomation**](../Model/ViewSmsInboundAutomation.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsInboundAutomations()`

```php
viewSmsInboundAutomations($content_type): \ClickSend\Model\ViewSmsInboundAutomations
```

View SMS Inbound Automations

_Get all inbound sms automations_  Get all inbound sms automations  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSmsInboundAutomations($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsInboundAutomations: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSmsInboundAutomations**](../Model/ViewSmsInboundAutomations.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsReceipts()`

```php
viewSmsReceipts($content_type, $page, $limit): \ClickSend\Model\ViewSmsReceipts
```

View SMS Receipts

Use this endpoint to retrieve <a href=\"https://help.clicksend.com/article/49eq1qdcui-how-do-i-receive-sms-delivery-receipts-delivery-status-updates\" target=\"_blank\">SMS delivery receipts</a> sent by your recipient.  To be able to view receipts, add a <a href=\"https://help.clicksend.com/en/articles/42317-delivery-notifications-reports\" target=\"_blank\">delivery report</a> rule with the Action set to **POLL** in the Dashboard, or use the [**Create SMS Delivery Receipt Rule**](/automations/sms/other/create-sms-delivery-receipt-rule) endpoint.  Control [pagination](/#pagination) with the _page_ and _limit_ query parameters to specify the page of results and the number of items returned.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$page = 1; // int | The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1.
$limit = 15; // int | The number of items to return per page. This parameter controls the size of each page of results. The default value is 15.

try {
    $result = $apiInstance->viewSmsReceipts($content_type, $page, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsReceipts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **page** | **int**| The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1. | [optional] [default to 1] |
| **limit** | **int**| The number of items to return per page. This parameter controls the size of each page of results. The default value is 15. | [optional] [default to 15] |

### Return type

[**\ClickSend\Model\ViewSmsReceipts**](../Model/ViewSmsReceipts.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSmsTemplates()`

```php
viewSmsTemplates($content_type, $page, $limit, $q, $order_by): \ClickSend\Model\ViewSmsTemplates
```

View SMS Templates

Use this endpoint to retrieve <a href=\"https://help.clicksend.com/article/9z9uloaz8y-sms-templates-for-different-industries\" target=\"_blank\">SMS templates</a>. You can filter the SMS templates result using the query parameters.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$page = 1; // int | The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1.
$limit = 15; // int | The number of items to return per page. This parameter controls the size of each page of results. The default value is 15.
$q = 'field_name'; // string | Allows filtering of results based on your search criteria. The query should be in the format `field_name:value`.  1. **Field Name**: The field within the SMS history you want to filter by. You can use the following fields:    - _template_id_ : The ID of the template   - _template_name_ : The name of the template   - _body_ : The body content of the template.          2. **Value**: The text or keyword you're searching for within the specified field. If left empty after the colon, the filter will look for all templates with any value in the **Field Name**.      For example, if you are searching for the template with the name of _sample_name_, the final query would look like this:     `q=template_name:sample_name`  <div class=\"info-box\">   <h4><i class=\"fas fa-info-circle\"></i> Note:</h4>   <div>    <p>Some characters have to be encoded. For example, if you are searching for SMS sent from the phone number +61437085284, your search query q would be:<br/></p>     <ul>       <li>q=from:%2B61437085284</li>     </ul>     <p>You can use the <a href=\"https://www.urlencoder.org/\" target=\"_blank\">URL encoder</a> to encode the text. If a character is not an alphanumeric character (A-Z, a-z, 0-9), it is typically either reserved or unsafe and should be encoded.</p>   </div> </div>
$order_by = 'template_id:asc'; // string | Specifies the field and order to sort the results by.  The value is composed of the field name followed by a colon and the sort direction (_asc_ for ascending or _desc_ for descending).  The default sort order is by _template_id_ in ascending order. You can use the following fields:      - _template_id_ : The ID of the Template - _template_name_ : The name of the Template - _body_ : The body content of the Template  For example, if you want to order by the _template_id_ in descending order, the query would look like this:    `order_by=template_id:desc`

try {
    $result = $apiInstance->viewSmsTemplates($content_type, $page, $limit, $q, $order_by);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSmsTemplates: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **page** | **int**| The page number to retrieve. Use this parameter to navigate through the [pagination](/#pagination) results. The default value is 1. | [optional] [default to 1] |
| **limit** | **int**| The number of items to return per page. This parameter controls the size of each page of results. The default value is 15. | [optional] [default to 15] |
| **q** | **string**| Allows filtering of results based on your search criteria. The query should be in the format &#x60;field_name:value&#x60;.  1. **Field Name**: The field within the SMS history you want to filter by. You can use the following fields:    - _template_id_ : The ID of the template   - _template_name_ : The name of the template   - _body_ : The body content of the template.          2. **Value**: The text or keyword you&#39;re searching for within the specified field. If left empty after the colon, the filter will look for all templates with any value in the **Field Name**.      For example, if you are searching for the template with the name of _sample_name_, the final query would look like this:     &#x60;q&#x3D;template_name:sample_name&#x60;  &lt;div class&#x3D;\&quot;info-box\&quot;&gt;   &lt;h4&gt;&lt;i class&#x3D;\&quot;fas fa-info-circle\&quot;&gt;&lt;/i&gt; Note:&lt;/h4&gt;   &lt;div&gt;    &lt;p&gt;Some characters have to be encoded. For example, if you are searching for SMS sent from the phone number +61437085284, your search query q would be:&lt;br/&gt;&lt;/p&gt;     &lt;ul&gt;       &lt;li&gt;q&#x3D;from:%2B61437085284&lt;/li&gt;     &lt;/ul&gt;     &lt;p&gt;You can use the &lt;a href&#x3D;\&quot;https://www.urlencoder.org/\&quot; target&#x3D;\&quot;_blank\&quot;&gt;URL encoder&lt;/a&gt; to encode the text. If a character is not an alphanumeric character (A-Z, a-z, 0-9), it is typically either reserved or unsafe and should be encoded.&lt;/p&gt;   &lt;/div&gt; &lt;/div&gt; | [optional] [default to &#39;field_name&#39;] |
| **order_by** | **string**| Specifies the field and order to sort the results by.  The value is composed of the field name followed by a colon and the sort direction (_asc_ for ascending or _desc_ for descending).  The default sort order is by _template_id_ in ascending order. You can use the following fields:      - _template_id_ : The ID of the Template - _template_name_ : The name of the Template - _body_ : The body content of the Template  For example, if you want to order by the _template_id_ in descending order, the query would look like this:    &#x60;order_by&#x3D;template_id:desc&#x60; | [optional] [default to &#39;template_id:asc&#39;] |

### Return type

[**\ClickSend\Model\ViewSmsTemplates**](../Model/ViewSmsTemplates.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSpecificSmsReceipt()`

```php
viewSpecificSmsReceipt($message_id, $content_type): \ClickSend\Model\ViewSpecificSmsReceipt
```

View Specific SMS Receipt

Use this endpoint to retrieve a specific <a href=\"https://help.clicksend.com/article/49eq1qdcui-how-do-i-receive-sms-delivery-receipts-delivery-status-updates\" target=\"_blank\">SMS delivery receipt</a>, including those that have been marked as read. When you send an SMS, a delivery receipt is generated and can be received.  This endpoint enables you to retrieve those receipts.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$message_id = 'message_id_example'; // string | The _message_id_ of the SMS delivery receipt to retrieve
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSpecificSmsReceipt($message_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SmsApi->viewSpecificSmsReceipt: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**| The _message_id_ of the SMS delivery receipt to retrieve | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSpecificSmsReceipt**](../Model/ViewSpecificSmsReceipt.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
