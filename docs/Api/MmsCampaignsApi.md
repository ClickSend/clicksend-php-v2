# ClickSend\MmsCampaignsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculateMmsCampaignPrice()**](MmsCampaignsApi.md#calculateMmsCampaignPrice) | **POST** /v3/mms-campaigns/price | Calculate MMS Campaign Price |
| [**cancelMmsCampaign()**](MmsCampaignsApi.md#cancelMmsCampaign) | **PUT** /v3/mms-campaigns/{mms_campaign_id}/cancel | Cancel MMS Campaign |
| [**sendMmsCampaign()**](MmsCampaignsApi.md#sendMmsCampaign) | **POST** /v3/mms-campaigns/send | Send MMS Campaign |
| [**updateMmsCampaign()**](MmsCampaignsApi.md#updateMmsCampaign) | **PUT** /v3/mms-campaigns/{mms_campaign_id} | Update MMS Campaign |
| [**viewAllMmsCampaigns()**](MmsCampaignsApi.md#viewAllMmsCampaigns) | **GET** /v3/mms-campaigns | View All MMS Campaigns |
| [**viewMmsCampaign()**](MmsCampaignsApi.md#viewMmsCampaign) | **GET** /v3/mms-campaigns/{mms_campaign_id} | View MMS Campaign |


## `calculateMmsCampaignPrice()`

```php
calculateMmsCampaignPrice($content_type, $body): \ClickSend\Model\CalculateMmsCampaignPrice
```

Calculate MMS Campaign Price

_Calculate price for mms campaign_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | list_id | integer(int32) | true | none | Your list id. | | name | string | true | none | Your campaign name. | | body | string | true | none | Your campaign message. | | from | string | true | [yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number) | Your sender id | | schedule | integer(int32) | false | none | Your schedule timestamp. | | subject | string | true | none | Subject of MMS campaign. | | media_file | string | true | none | URL pointing to media file. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\MmsCampaignsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$body = array('key' => new \stdClass); // object

try {
    $result = $apiInstance->calculateMmsCampaignPrice($content_type, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsCampaignsApi->calculateMmsCampaignPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **body** | **object**|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateMmsCampaignPrice**](../Model/CalculateMmsCampaignPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelMmsCampaign()`

```php
cancelMmsCampaign($mms_campaign_id, $content_type, $calculate_sms_campaign_price_request): \ClickSend\Model\CancelMmsCampaign
```

Cancel MMS Campaign

_Cancel mms campaign_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | mms_campaign_id | path | integer(int32) | true | ID of MMS Campaign to cancel |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\MmsCampaignsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$mms_campaign_id = 'mms_campaign_id_example'; // string
$content_type = application/json; // string
$calculate_sms_campaign_price_request = new \ClickSend\Model\CalculateSmsCampaignPriceRequest(); // \ClickSend\Model\CalculateSmsCampaignPriceRequest

try {
    $result = $apiInstance->cancelMmsCampaign($mms_campaign_id, $content_type, $calculate_sms_campaign_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsCampaignsApi->cancelMmsCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mms_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **calculate_sms_campaign_price_request** | [**\ClickSend\Model\CalculateSmsCampaignPriceRequest**](../Model/CalculateSmsCampaignPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CancelMmsCampaign**](../Model/CancelMmsCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendMmsCampaign()`

```php
sendMmsCampaign($content_type, $send_mms_campaign_request): \ClickSend\Model\SendMmsCampaign
```

Send MMS Campaign

_Create mms campaign_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | list_id | integer(int32) | true | none | Your list id. | | name | string | true | none | Your campaign name. | | body | string | true | none | Your campaign message. | | from | string | true | [yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number) | Your sender id | | schedule | integer(int32) | false | none | Your schedule timestamp. | | subject | string | true | none | Subject of MMS campaign. | | media_file | string | true | none | URL pointing to media file. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\MmsCampaignsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_mms_campaign_request = new \ClickSend\Model\SendMmsCampaignRequest(); // \ClickSend\Model\SendMmsCampaignRequest

try {
    $result = $apiInstance->sendMmsCampaign($content_type, $send_mms_campaign_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsCampaignsApi->sendMmsCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_mms_campaign_request** | [**\ClickSend\Model\SendMmsCampaignRequest**](../Model/SendMmsCampaignRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendMmsCampaign**](../Model/SendMmsCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateMmsCampaign()`

```php
updateMmsCampaign($mms_campaign_id, $content_type, $calculate_sms_campaign_price_request): \ClickSend\Model\UpdateMmsCampaign
```

Update MMS Campaign

_Update mms campaign_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | mms_campaign_id | path | integer(int32) | true | ID of MMS campaign to update |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | list_id | integer(int32) | true | none | Your list id. | | name | string | true | none | Your campaign name. | | body | string | true | none | Your campaign message. | | from | string | true | [yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number) | Your sender id | | schedule | integer(int32) | false | none | Your schedule timestamp. | | subject | string | true | none | Subject of MMS campaign. | | media_file | string | true | none | URL pointing to media file. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\MmsCampaignsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$mms_campaign_id = 'mms_campaign_id_example'; // string
$content_type = application/json; // string
$calculate_sms_campaign_price_request = new \ClickSend\Model\CalculateSmsCampaignPriceRequest(); // \ClickSend\Model\CalculateSmsCampaignPriceRequest

try {
    $result = $apiInstance->updateMmsCampaign($mms_campaign_id, $content_type, $calculate_sms_campaign_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsCampaignsApi->updateMmsCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mms_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **calculate_sms_campaign_price_request** | [**\ClickSend\Model\CalculateSmsCampaignPriceRequest**](../Model/CalculateSmsCampaignPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateMmsCampaign**](../Model/UpdateMmsCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAllMmsCampaigns()`

```php
viewAllMmsCampaigns($content_type): \ClickSend\Model\ViewAllMmsCampaigns
```

View All MMS Campaigns

_Get list of mms campaigns_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\MmsCampaignsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAllMmsCampaigns($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsCampaignsApi->viewAllMmsCampaigns: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAllMmsCampaigns**](../Model/ViewAllMmsCampaigns.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewMmsCampaign()`

```php
viewMmsCampaign($mms_campaign_id, $content_type): \ClickSend\Model\ViewMmsCampaign
```

View MMS Campaign

_Get specific mms campaign_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | mms_campaign_id | path | integer(int32) | true | ID of MMS campaign to retrieve |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\MmsCampaignsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$mms_campaign_id = 'mms_campaign_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewMmsCampaign($mms_campaign_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MmsCampaignsApi->viewMmsCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mms_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewMmsCampaign**](../Model/ViewMmsCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
