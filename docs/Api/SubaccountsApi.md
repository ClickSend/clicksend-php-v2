# ClickSend\SubaccountsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createSubaccount()**](SubaccountsApi.md#createSubaccount) | **POST** /v3/subaccounts | Create Subaccount |
| [**deleteSubaccount()**](SubaccountsApi.md#deleteSubaccount) | **DELETE** /v3/subaccounts/{subaccount_id} | Delete Subaccount |
| [**generateNewApiKey()**](SubaccountsApi.md#generateNewApiKey) | **PUT** /v3/subaccounts/{subaccount_id}/regen-api-key | Generate New API Key |
| [**updateSubaccount()**](SubaccountsApi.md#updateSubaccount) | **PUT** /v3/subaccounts/{subaccount_id} | Update Subaccount |
| [**viewSpecificSubaccount()**](SubaccountsApi.md#viewSpecificSubaccount) | **GET** /v3/subaccounts/{subaccount_id} | View Specific Subaccount |
| [**viewSubaccounts()**](SubaccountsApi.md#viewSubaccounts) | **GET** /v3/subaccounts | View Subaccounts |


## `createSubaccount()`

```php
createSubaccount($content_type, $create_subaccount_request): \ClickSend\Model\CreateSubaccount
```

Create Subaccount

_Create new subaccount_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | api_username | string | true | none | Your new api username. | | password | string | true | none | Your new password | | email | string | true | none | Your new email. | | phone_number | string | true | none | Your phone number in [E.164](https://en.wikipedia.org/wiki/E.164) format. | | first_name | string | true | none | Your firstname | | last_name | string | true | none | Your lastname | | access_users | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_billing | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_reporting | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_contacts | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_settings | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SubaccountsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_subaccount_request = new \ClickSend\Model\CreateSubaccountRequest(); // \ClickSend\Model\CreateSubaccountRequest

try {
    $result = $apiInstance->createSubaccount($content_type, $create_subaccount_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubaccountsApi->createSubaccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_subaccount_request** | [**\ClickSend\Model\CreateSubaccountRequest**](../Model/CreateSubaccountRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateSubaccount**](../Model/CreateSubaccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSubaccount()`

```php
deleteSubaccount($subaccount_id, $content_type): \ClickSend\Model\DeleteSubaccount
```

Delete Subaccount

_Delete a subaccount_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | subaccount_id | path | integer(int32) | true | ID of subaccount to delete |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SubaccountsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$subaccount_id = 'subaccount_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteSubaccount($subaccount_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubaccountsApi->deleteSubaccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **subaccount_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteSubaccount**](../Model/DeleteSubaccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `generateNewApiKey()`

```php
generateNewApiKey($subaccount_id, $content_type, $generate_new_api_key_request): \ClickSend\Model\GenerateNewApiKey
```

Generate New API Key

_Regenerate an API Key_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | subaccount_id | path | integer(int32) | true | ID of subaccount to regenerate API key for |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SubaccountsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$subaccount_id = 'subaccount_id_example'; // string
$content_type = application/json; // string
$generate_new_api_key_request = new \ClickSend\Model\GenerateNewApiKeyRequest(); // \ClickSend\Model\GenerateNewApiKeyRequest

try {
    $result = $apiInstance->generateNewApiKey($subaccount_id, $content_type, $generate_new_api_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubaccountsApi->generateNewApiKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **subaccount_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **generate_new_api_key_request** | [**\ClickSend\Model\GenerateNewApiKeyRequest**](../Model/GenerateNewApiKeyRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\GenerateNewApiKey**](../Model/GenerateNewApiKey.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateSubaccount()`

```php
updateSubaccount($subaccount_id, $content_type, $update_subaccount_request): \ClickSend\Model\UpdateSubaccount
```

Update Subaccount

_Update subaccount_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | subaccount_id | path | integer(int32) | true | ID of subaccount to update |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | api_username | string | true | none | Your new api username. | | password | string | true | none | Your new password | | email | string | true | none | Your new email. | | phone_number | string | true | none | Your phone number in [E.164](https://en.wikipedia.org/wiki/E.164) format. | | first_name | string | true | none | Your firstname | | last_name | string | true | none | Your lastname | | access_users | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_billing | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_reporting | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_contacts | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. | | access_settings | integer(int1) | false | none | Flag value must be 1 for yes or 0 for no. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SubaccountsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$subaccount_id = 'subaccount_id_example'; // string
$content_type = application/json; // string
$update_subaccount_request = new \ClickSend\Model\UpdateSubaccountRequest(); // \ClickSend\Model\UpdateSubaccountRequest

try {
    $result = $apiInstance->updateSubaccount($subaccount_id, $content_type, $update_subaccount_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubaccountsApi->updateSubaccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **subaccount_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_subaccount_request** | [**\ClickSend\Model\UpdateSubaccountRequest**](../Model/UpdateSubaccountRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateSubaccount**](../Model/UpdateSubaccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSpecificSubaccount()`

```php
viewSpecificSubaccount($subaccount_id, $content_type): \ClickSend\Model\ViewSpecificSubaccount
```

View Specific Subaccount

_Get specific subaccount_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | subaccount_id | path | integer(int32) | true | ID of subaccount to get |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SubaccountsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$subaccount_id = 'subaccount_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSpecificSubaccount($subaccount_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubaccountsApi->viewSpecificSubaccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **subaccount_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSpecificSubaccount**](../Model/ViewSpecificSubaccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSubaccounts()`

```php
viewSubaccounts($content_type): \ClickSend\Model\ViewSubaccounts
```

View Subaccounts

_Get all subaccounts_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\SubaccountsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSubaccounts($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SubaccountsApi->viewSubaccounts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSubaccounts**](../Model/ViewSubaccounts.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
