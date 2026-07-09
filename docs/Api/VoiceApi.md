# ClickSend\VoiceApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createVoiceDeliveryReceiptRule()**](VoiceApi.md#createVoiceDeliveryReceiptRule) | **POST** /v3/automations/voice/receipts | Create Voice Delivery Receipt Rule |
| [**deleteVoiceDeliveryReceiptRule()**](VoiceApi.md#deleteVoiceDeliveryReceiptRule) | **DELETE** /v3/automations/voice/receipts/{receipt_rule_id} | Delete Voice Delivery Receipt Rule |
| [**updateVoiceDeliveryReceiptRule()**](VoiceApi.md#updateVoiceDeliveryReceiptRule) | **PUT** /v3/automations/voice/receipts/{receipt_rule_id} | Update Voice Delivery Receipt Rule |
| [**viewVoiceDeliveryReceiptRule()**](VoiceApi.md#viewVoiceDeliveryReceiptRule) | **GET** /v3/automations/voice/receipts/{receipt_rule_id} | View Voice Delivery Receipt Rule |
| [**viewVoiceDeliveryReceiptRules()**](VoiceApi.md#viewVoiceDeliveryReceiptRules) | **GET** /v3/automations/voice/receipts | View Voice Delivery Receipt Rules |


## `createVoiceDeliveryReceiptRule()`

```php
createVoiceDeliveryReceiptRule($content_type, $create_sms_delivery_receipt_rule_request): \ClickSend\Model\CreateVoiceDeliveryReceiptRule
```

Create Voice Delivery Receipt Rule

_Create voice delivery receipt automations_  Create voice delivery receipt automations  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_sms_delivery_receipt_rule_request = new \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->createVoiceDeliveryReceiptRule($content_type, $create_sms_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceApi->createVoiceDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_sms_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest**](../Model/CreateSmsDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateVoiceDeliveryReceiptRule**](../Model/CreateVoiceDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteVoiceDeliveryReceiptRule()`

```php
deleteVoiceDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\DeleteVoiceDeliveryReceiptRule
```

Delete Voice Delivery Receipt Rule

_Delete voice delivery receipt automation_  Delete voice delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteVoiceDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceApi->deleteVoiceDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteVoiceDeliveryReceiptRule**](../Model/DeleteVoiceDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateVoiceDeliveryReceiptRule()`

```php
updateVoiceDeliveryReceiptRule($receipt_rule_id, $content_type, $create_sms_delivery_receipt_rule_request): \ClickSend\Model\UpdateVoiceDeliveryReceiptRule
```

Update Voice Delivery Receipt Rule

_Update voice delivery receipt automation_  Update voice delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string
$create_sms_delivery_receipt_rule_request = new \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->updateVoiceDeliveryReceiptRule($receipt_rule_id, $content_type, $create_sms_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceApi->updateVoiceDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **create_sms_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest**](../Model/CreateSmsDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateVoiceDeliveryReceiptRule**](../Model/UpdateVoiceDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewVoiceDeliveryReceiptRule()`

```php
viewVoiceDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\ViewVoiceDeliveryReceiptRule
```

View Voice Delivery Receipt Rule

_Get specific voice delivery receipt automation_  Get specific voice delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewVoiceDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceApi->viewVoiceDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewVoiceDeliveryReceiptRule**](../Model/ViewVoiceDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewVoiceDeliveryReceiptRules()`

```php
viewVoiceDeliveryReceiptRules($content_type): \ClickSend\Model\ViewVoiceDeliveryReceiptRules
```

View Voice Delivery Receipt Rules

_Get all voice delivery receipt automations_  Get all voice delivery receipt automations  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewVoiceDeliveryReceiptRules($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceApi->viewVoiceDeliveryReceiptRules: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewVoiceDeliveryReceiptRules**](../Model/ViewVoiceDeliveryReceiptRules.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
