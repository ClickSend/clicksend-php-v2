# ClickSend\ManagementApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**viewAccountDetails()**](ManagementApi.md#viewAccountDetails) | **GET** /v3/account | View Account Details |
| [**viewAccountUsage()**](ManagementApi.md#viewAccountUsage) | **GET** /v3/account/usage/{year}/{month}/subaccount | View Account Usage |


## `viewAccountDetails()`

```php
viewAccountDetails($content_type): \ClickSend\Model\ViewAccountDetails
```

View Account Details

_Get account information_  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/#pagination\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ManagementApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAccountDetails($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ManagementApi->viewAccountDetails: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAccountDetails**](../Model/ViewAccountDetails.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAccountUsage()`

```php
viewAccountUsage($year, $month, $content_type): \ClickSend\Model\ViewAccountUsage
```

View Account Usage

_Get account usage_  | **Name** | **Type** | **Required** | **Restrictions** | **Description** | | --- | --- | --- | --- | --- | | year | string | true | none | Your account usage year. Example: 2019 | | month | string | true | none | Your account usage month. Example: 4 |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/#pagination\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ManagementApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$year = 'year_example'; // string
$month = 'month_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAccountUsage($year, $month, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ManagementApi->viewAccountUsage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **year** | **string**|  | |
| **month** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAccountUsage**](../Model/ViewAccountUsage.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
