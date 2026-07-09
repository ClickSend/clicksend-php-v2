# ClickSend\FaxApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculateFaxPrice()**](FaxApi.md#calculateFaxPrice) | **POST** /v3/fax/price | Calculate Fax Price |
| [**createFaxDeliveryReceiptRule()**](FaxApi.md#createFaxDeliveryReceiptRule) | **POST** /v3/automations/fax/receipts | Create FAX Delivery Receipt Rule |
| [**createFaxInboundRule()**](FaxApi.md#createFaxInboundRule) | **POST** /v3/automations/fax/inbound | Create Fax Inbound Rule |
| [**deleteFaxDeliveryReceiptRule()**](FaxApi.md#deleteFaxDeliveryReceiptRule) | **DELETE** /v3/automations/fax/receipts/{receipt_rule_id} | Delete FAX Delivery Receipt Rule |
| [**deleteFaxInboundRule()**](FaxApi.md#deleteFaxInboundRule) | **DELETE** /v3/automations/fax/inbound/{inbound_rule_id} | Delete Fax Inbound Rule |
| [**sendFax()**](FaxApi.md#sendFax) | **POST** /v3/fax/send | Send Fax |
| [**updateFaxDeliveryReceiptRule()**](FaxApi.md#updateFaxDeliveryReceiptRule) | **PUT** /v3/automations/fax/receipts/{receipt_rule_id} | Update FAX Delivery Receipt Rule |
| [**updateFaxInboundRule()**](FaxApi.md#updateFaxInboundRule) | **PUT** /v3/automations/fax/inbound/{inbound_rule_id} | Update Fax Inbound Rule |
| [**viewFaxDeliveryReceiptRule()**](FaxApi.md#viewFaxDeliveryReceiptRule) | **GET** /v3/automations/fax/receipts/{receipt_rule_id} | View FAX Delivery Receipt Rule |
| [**viewFaxDeliveryReceiptRules()**](FaxApi.md#viewFaxDeliveryReceiptRules) | **GET** /v3/automations/fax/receipts | View FAX Delivery Receipt Rules |
| [**viewFaxHistory()**](FaxApi.md#viewFaxHistory) | **GET** /v3/fax/history | View Fax History |
| [**viewFaxInboundRule()**](FaxApi.md#viewFaxInboundRule) | **GET** /v3/automations/fax/inbound/{inbound_rule_id} | View Fax Inbound Rule |
| [**viewFaxInboundRules()**](FaxApi.md#viewFaxInboundRules) | **GET** /v3/automations/fax/inbound | View Fax Inbound Rules |
| [**viewFaxReceipts()**](FaxApi.md#viewFaxReceipts) | **GET** /v3/fax/receipts | View Fax Receipts |
| [**viewSpecificFaxReceipt()**](FaxApi.md#viewSpecificFaxReceipt) | **GET** /v3/fax/receipts/{message_id} | View Specific Fax Receipt |


## `calculateFaxPrice()`

```php
calculateFaxPrice($content_type, $calculate_fax_price_request): \ClickSend\Model\CalculateFaxPrice
```

Calculate Fax Price

_Calculate Total Price for Fax Messages sent_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | file_url | string | true | none | URL of file to send | | source | string | true | none | Your method of sending e.g. 'wordpress', 'php', 'c#'. | | to | string | true | none | Recipient fax number in [E.164](https://en.wikipedia.org/wiki/E.164) format. | | list_id | integer(int32) | false | none | Your list ID if sending to a whole list. Can be used instead of 'to'. | | from | string | true | [yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number) | Your sender id. Must be a valid fax number. | | schedule | integer(int32) | false | none | Leave blank for immediate delivery. Your schedule time in unix format [http://help.clicksend.com/what-is-a-unix-timestamp](http://help.clicksend.com/what-is-a-unix-timestamp) | | custom_string | string | false | none | Your reference. Will be passed back with all replies and delivery reports. | | country | string | false | none | ISO alpha-2 character country code e.g. 'US', we use this to format the recipient number if it's not in international format. | | from_email | string | false | none | An email address where the reply should be emailed to. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$calculate_fax_price_request = new \ClickSend\Model\CalculateFaxPriceRequest(); // \ClickSend\Model\CalculateFaxPriceRequest

try {
    $result = $apiInstance->calculateFaxPrice($content_type, $calculate_fax_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->calculateFaxPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **calculate_fax_price_request** | [**\ClickSend\Model\CalculateFaxPriceRequest**](../Model/CalculateFaxPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateFaxPrice**](../Model/CalculateFaxPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createFaxDeliveryReceiptRule()`

```php
createFaxDeliveryReceiptRule($content_type, $create_fax_delivery_receipt_rule_request): \ClickSend\Model\CreateFaxDeliveryReceiptRule
```

Create FAX Delivery Receipt Rule

_Create fax delivery receipt automations_  Create fax delivery receipt automations  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_fax_delivery_receipt_rule_request = new \ClickSend\Model\CreateFaxDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateFaxDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->createFaxDeliveryReceiptRule($content_type, $create_fax_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->createFaxDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_fax_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateFaxDeliveryReceiptRuleRequest**](../Model/CreateFaxDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateFaxDeliveryReceiptRule**](../Model/CreateFaxDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createFaxInboundRule()`

```php
createFaxInboundRule($content_type, $create_fax_inbound_rule_request): \ClickSend\Model\CreateFaxInboundRule
```

Create Fax Inbound Rule

_Create new inbound fax automation_  Create new inbound fax automation  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | dedicated_number | string | true | none | Dedicated Number. Can be '\\*' to apply to all numbers. | | rule_name | string | true | none | Rule Name. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_fax_inbound_rule_request = new \ClickSend\Model\CreateFaxInboundRuleRequest(); // \ClickSend\Model\CreateFaxInboundRuleRequest

try {
    $result = $apiInstance->createFaxInboundRule($content_type, $create_fax_inbound_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->createFaxInboundRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_fax_inbound_rule_request** | [**\ClickSend\Model\CreateFaxInboundRuleRequest**](../Model/CreateFaxInboundRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateFaxInboundRule**](../Model/CreateFaxInboundRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteFaxDeliveryReceiptRule()`

```php
deleteFaxDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\DeleteFaxDeliveryReceiptRule
```

Delete FAX Delivery Receipt Rule

_Delete fax delivery receipt automation_  Delete fax delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteFaxDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->deleteFaxDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteFaxDeliveryReceiptRule**](../Model/DeleteFaxDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteFaxInboundRule()`

```php
deleteFaxInboundRule($inbound_rule_id, $content_type): \ClickSend\Model\DeleteFaxInboundRule
```

Delete Fax Inbound Rule

_Delete inbound fax automation_  Delete inbound fax automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | inbound_rule_id | path | integer(int32) | true | Inbound rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$inbound_rule_id = 'inbound_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteFaxInboundRule($inbound_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->deleteFaxInboundRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **inbound_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteFaxInboundRule**](../Model/DeleteFaxInboundRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendFax()`

```php
sendFax($content_type, $send_fax_request): \ClickSend\Model\SendFax
```

Send Fax

### **Supported File Types**  - Supported file types are listed below. If you need to convert a file to a supported format, it can be first passed to our uploads endpoint: `/uploads?convert=fax` - This will return a URL to the converted pdf file that can be used in the /fax/send endpoint. - Contact us to add support for any other file type.       ### Documents  | File type | Required to be passed to uploads endpoint first? | | --- | --- | | pdf | No | | docx | Yes | | doc | Yes | | rtf | Yes |  _Send a fax using supplied supported file-types._  ### **Letter File Options**  ### Use existing URL  With this option, you can use an existing URL to a `pdf` document. For example, you might generate the `pdf` on your server.  When using an existing url make sure that it is publicly accessible as it will not work if it is private.  ### Upload File to Our Server  With this option, you can use the [/uploads](/#upload-media-file) endpoint to upload the document. The `/uploads` endpoint returns a URL that can be used in the `/fax/send` endpoint.  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | file_url | string | true | none | URL of file to send | | source | string | true | none | Your method of sending e.g. 'wordpress', 'php', 'c#'. | | to | string | true | none | Recipient fax number in [E.164](https://en.wikipedia.org/wiki/E.164) format. | | list_id | integer(int32) | false | none | Your list ID if sending to a whole list. Can be used instead of 'to'. | | from | string | true | [yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number) | Your sender id. Must be a valid fax number. | | schedule | integer(int32) | false | none | Leave blank for immediate delivery. Your schedule time in unix format [http://help.clicksend.com/what-is-a-unix-timestamp](http://help.clicksend.com/what-is-a-unix-timestamp) | | custom_string | string | false | none | Your reference. Will be passed back with all replies and delivery reports. | | country | string | false | none | ISO alpha-2 character country code e.g. 'US', we use this to format the recipient number if it's not in international format. | | from_email | string | false | none | An email address where the reply should be emailed to. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_fax_request = new \ClickSend\Model\SendFaxRequest(); // \ClickSend\Model\SendFaxRequest

try {
    $result = $apiInstance->sendFax($content_type, $send_fax_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->sendFax: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_fax_request** | [**\ClickSend\Model\SendFaxRequest**](../Model/SendFaxRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendFax**](../Model/SendFax.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateFaxDeliveryReceiptRule()`

```php
updateFaxDeliveryReceiptRule($receipt_rule_id, $content_type, $update_fax_delivery_receipt_rule_request): \ClickSend\Model\UpdateFaxDeliveryReceiptRule
```

Update FAX Delivery Receipt Rule

_Update fax delivery receipt automation_  Update fax delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string
$update_fax_delivery_receipt_rule_request = new \ClickSend\Model\UpdateFaxDeliveryReceiptRuleRequest(); // \ClickSend\Model\UpdateFaxDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->updateFaxDeliveryReceiptRule($receipt_rule_id, $content_type, $update_fax_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->updateFaxDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_fax_delivery_receipt_rule_request** | [**\ClickSend\Model\UpdateFaxDeliveryReceiptRuleRequest**](../Model/UpdateFaxDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateFaxDeliveryReceiptRule**](../Model/UpdateFaxDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateFaxInboundRule()`

```php
updateFaxInboundRule($inbound_rule_id, $content_type, $create_fax_inbound_rule_request): \ClickSend\Model\UpdateFaxInboundRule
```

Update Fax Inbound Rule

_Update inbound fax automation_  Update inbound fax automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | inbound_rule_id | path | integer(int32) | true | Inbound rule id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | dedicated_number | string | true | none | Dedicated Number. Can be '\\*' to apply to all numbers. | | rule_name | string | true | none | Rule Name. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$inbound_rule_id = 'inbound_rule_id_example'; // string
$content_type = application/json; // string
$create_fax_inbound_rule_request = new \ClickSend\Model\CreateFaxInboundRuleRequest(); // \ClickSend\Model\CreateFaxInboundRuleRequest

try {
    $result = $apiInstance->updateFaxInboundRule($inbound_rule_id, $content_type, $create_fax_inbound_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->updateFaxInboundRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **inbound_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **create_fax_inbound_rule_request** | [**\ClickSend\Model\CreateFaxInboundRuleRequest**](../Model/CreateFaxInboundRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateFaxInboundRule**](../Model/UpdateFaxInboundRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewFaxDeliveryReceiptRule()`

```php
viewFaxDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\ViewFaxDeliveryReceiptRule
```

View FAX Delivery Receipt Rule

_Get specific fax delivery receipt automation_  Get specific fax delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewFaxDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewFaxDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewFaxDeliveryReceiptRule**](../Model/ViewFaxDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewFaxDeliveryReceiptRules()`

```php
viewFaxDeliveryReceiptRules($content_type): \ClickSend\Model\ViewFaxDeliveryReceiptRules
```

View FAX Delivery Receipt Rules

_Get all fax delivery receipt automations_  Get all fax delivery receipt automations  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewFaxDeliveryReceiptRules($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewFaxDeliveryReceiptRules: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewFaxDeliveryReceiptRules**](../Model/ViewFaxDeliveryReceiptRules.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewFaxHistory()`

```php
viewFaxHistory($content_type): \ClickSend\Model\ViewFaxHistory
```

View Fax History

_Get a list of Fax History._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | date_from | query | integer(int32) | false | Start date (Unix Timestamp e.g. 1436849372) | | date_to | query | integer(int32) | false | End date (Unix Timestamp e.g. 1436879372) | | q | query | string | false | Custom query Example: status:Sent,status_code:201. | | order | query | string | false | Order result by Example: date_added:desc,list_id:desc. | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewFaxHistory($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewFaxHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewFaxHistory**](../Model/ViewFaxHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewFaxInboundRule()`

```php
viewFaxInboundRule($inbound_rule_id, $content_type): \ClickSend\Model\ViewFaxInboundRule
```

View Fax Inbound Rule

_Get specific inbound fax automation_  Get specific inbound fax automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | inbound_rule_id | path | integer(int32) | true | Inbound rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$inbound_rule_id = 'inbound_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewFaxInboundRule($inbound_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewFaxInboundRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **inbound_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewFaxInboundRule**](../Model/ViewFaxInboundRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewFaxInboundRules()`

```php
viewFaxInboundRules($content_type): \ClickSend\Model\ViewFaxInboundRules
```

View Fax Inbound Rules

_Get all inbound fax automations_  Get all inbound fax automations  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewFaxInboundRules($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewFaxInboundRules: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewFaxInboundRules**](../Model/ViewFaxInboundRules.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewFaxReceipts()`

```php
viewFaxReceipts($content_type): \ClickSend\Model\ViewFaxReceipts
```

View Fax Receipts

_Get List of Fax Receipts_  **Push Delivery Receipts**  If you prefer, we can push message replies to your server as they arrive with us.  1. Log into your account. 2. Click on your profile on the top right. 3. Then click on the Messaging Settings option. 4. Click on Fax then Delivery Reports. 5. Click the 'Add New Rule' button. 6. Select the 'URL' action. 7. Enter the URL and click 'Save'.       The following variables will be posted to the URL specified:  | Variable | Description | | --- | --- | | `timestamp_send` | Timestamp of the original send request in UNIX format. e.g 1439173980 | | `timestamp` | Timestamp of delivery report in UNIX format. e.g 1439173981 | | `message_id` | Message ID, returned when originally sending the message. | | `status` | Delivered or Undelivered | | `status_code` | Status code. Refer to 'Fax Delivery Status Codes' in docs. | | `status_text` | Status text. | | `error_code` | Error code. | | `error_text` | Error text. | | `custom_string` | A custom string used when sending the original message. | | `user_id` | The user ID of the user who sent the message. | | `subaccount_id` | The subaccount ID of the user who sent the message. | | `message_type` | 'fax' (constant). |  **Pull Delivery Receipts**  Receive delivery reports by polling. You can poll our server and retrieve delivery reports at a time that suits you.  1. Log into your account. 2. Click on your profile on the top right. 3. Then click on the Messaging Settings option. 4. Click on Fax then Delivery Rules. 5. Click the 'Add New Rule' button. 6. Select the 'Poll' action. 7. Then click 'Save'.       Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewFaxReceipts($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewFaxReceipts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewFaxReceipts**](../Model/ViewFaxReceipts.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSpecificFaxReceipt()`

```php
viewSpecificFaxReceipt($message_id, $content_type): \ClickSend\Model\ViewSpecificFaxReceipt
```

View Specific Fax Receipt

_Get a single fax receipt based on message id._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | message_id | path | string | true | ID of the message receipt to retrieve |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\FaxApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$message_id = 'message_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSpecificFaxReceipt($message_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling FaxApi->viewSpecificFaxReceipt: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSpecificFaxReceipt**](../Model/ViewSpecificFaxReceipt.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
