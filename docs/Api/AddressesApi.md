# ClickSend\AddressesApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createReturnAddress()**](AddressesApi.md#createReturnAddress) | **POST** /v3/post/return-addresses | Create Return Address |
| [**deleteReturnAddress()**](AddressesApi.md#deleteReturnAddress) | **DELETE** /v3/post/return-addresses/{return_address_id} | Delete Return Address |
| [**updateReturnAddress()**](AddressesApi.md#updateReturnAddress) | **PUT** /v3/post/return-addresses/{return_address_id} | Update Return Address |
| [**viewSpecificReturnAddress()**](AddressesApi.md#viewSpecificReturnAddress) | **GET** /v3/post/return-addresses/{return_address_id} | View Specific Return Address |
| [**viewYourReturnAddresses()**](AddressesApi.md#viewYourReturnAddresses) | **GET** /v3/post/return-addresses | View Your Return Addresses |


## `createReturnAddress()`

```php
createReturnAddress($content_type, $create_return_address_request): \ClickSend\Model\CreateReturnAddress
```

Create Return Address

_Create post return address_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | address_name | string | true | none | Your address name. | | address_line_1 | string | true | none | Your address line 1 | | address_city | string | true | none | Your city | | address_postal_code | string | true | none | Your postal code | | address_country | string | true | none | Your country | | address_line_2 | string | false | none | Your address line 2 | | address_state | string | false | none | Your state |    Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.    <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AddressesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_return_address_request = new \ClickSend\Model\CreateReturnAddressRequest(); // \ClickSend\Model\CreateReturnAddressRequest

try {
    $result = $apiInstance->createReturnAddress($content_type, $create_return_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddressesApi->createReturnAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_return_address_request** | [**\ClickSend\Model\CreateReturnAddressRequest**](../Model/CreateReturnAddressRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateReturnAddress**](../Model/CreateReturnAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteReturnAddress()`

```php
deleteReturnAddress($return_address_id, $content_type): \ClickSend\Model\DeleteReturnAddress
```

Delete Return Address

_Delete specific post return address_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | return_address_id | path | integer(int32) | true | Return address ID |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AddressesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$return_address_id = 'return_address_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteReturnAddress($return_address_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddressesApi->deleteReturnAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **return_address_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteReturnAddress**](../Model/DeleteReturnAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateReturnAddress()`

```php
updateReturnAddress($return_address_id, $content_type, $update_return_address_request): \ClickSend\Model\UpdateReturnAddress
```

Update Return Address

_Update post return address_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | return_address_id | path | integer(int32) | true | Return address ID |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | address_name | string | true | none | Your address name. | | address_line_1 | string | true | none | Your address line 1 | | address_city | string | true | none | Your city | | address_postal_code | string | true | none | Your postal code | | address_country | string | true | none | Your country | | address_line_2 | string | false | none | Your address line 2 | | address_state | string | false | none | Your state |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AddressesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$return_address_id = 'return_address_id_example'; // string
$content_type = application/json; // string
$update_return_address_request = new \ClickSend\Model\UpdateReturnAddressRequest(); // \ClickSend\Model\UpdateReturnAddressRequest

try {
    $result = $apiInstance->updateReturnAddress($return_address_id, $content_type, $update_return_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddressesApi->updateReturnAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **return_address_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_return_address_request** | [**\ClickSend\Model\UpdateReturnAddressRequest**](../Model/UpdateReturnAddressRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateReturnAddress**](../Model/UpdateReturnAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSpecificReturnAddress()`

```php
viewSpecificReturnAddress($return_address_id, $content_type): \ClickSend\Model\ViewSpecificReturnAddress
```

View Specific Return Address

_Get specific post return address_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | return_address_id | path | integer(int32) | true | Return address ID |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AddressesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$return_address_id = 'return_address_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSpecificReturnAddress($return_address_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddressesApi->viewSpecificReturnAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **return_address_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSpecificReturnAddress**](../Model/ViewSpecificReturnAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewYourReturnAddresses()`

```php
viewYourReturnAddresses($content_type): \ClickSend\Model\ViewYourReturnAddresses
```

View Your Return Addresses

_Get list of post return addresses_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AddressesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewYourReturnAddresses($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddressesApi->viewYourReturnAddresses: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewYourReturnAddresses**](../Model/ViewYourReturnAddresses.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
