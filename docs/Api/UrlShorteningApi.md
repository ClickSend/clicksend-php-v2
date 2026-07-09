# ClickSend\UrlShorteningApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**shortUrlGetStatistics()**](UrlShorteningApi.md#shortUrlGetStatistics) | **GET** /v3/short-url/statistics/{source}/{source_id} | Get Statistics |
| [**shortUrlGetTracking()**](UrlShorteningApi.md#shortUrlGetTracking) | **GET** /v3/short-url/tracking/{long_url_id} | Get Tracking |


## `shortUrlGetStatistics()`

```php
shortUrlGetStatistics($source, $source_id, $content_type): \ClickSend\Model\GetStatistics
```

Get Statistics

Use this endpoint to get the aggregated statistics for a shortened URL. This allows you to track the total number of clicks on the link. You can gather details such as the device type and where it was opened from as well.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\UrlShorteningApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$source = 'source_example'; // string | Source of the request.
$source_id = 'source_id_example'; // string | ID of the source (e.g. message ID).
$content_type = application/json; // string

try {
    $result = $apiInstance->shortUrlGetStatistics($source, $source_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UrlShorteningApi->shortUrlGetStatistics: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **source** | **string**| Source of the request. | |
| **source_id** | **string**| ID of the source (e.g. message ID). | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\GetStatistics**](../Model/GetStatistics.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `shortUrlGetTracking()`

```php
shortUrlGetTracking($long_url_id, $content_type): \ClickSend\Model\GetTracking
```

Get Tracking

Use this endpoint to track how individual recipients interact with the link.  It returns data from the most recent click, including statistics such as how many times they’ve visited the link and when it was last opened. To use this endpoint, reference the _long_url_id_ provided in the [GET /short-url/statistics](/messaging/url-shortening/other/short-url-get-statistics) endpoint.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\UrlShorteningApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$long_url_id = 'long_url_id_example'; // string | ID of the long URL (uniquely defined by the source, source ID, and long URL). Obtained from the GET statistics endpoint.
$content_type = application/json; // string

try {
    $result = $apiInstance->shortUrlGetTracking($long_url_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UrlShorteningApi->shortUrlGetTracking: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **long_url_id** | **string**| ID of the long URL (uniquely defined by the source, source ID, and long URL). Obtained from the GET statistics endpoint. | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\GetTracking**](../Model/GetTracking.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
