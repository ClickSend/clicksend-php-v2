# ClickSend\PostcardsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculatePostcardPrice()**](PostcardsApi.md#calculatePostcardPrice) | **POST** /v3/post/postcards/price | Calculate Postcard Price |
| [**cancelScheduledPostcard()**](PostcardsApi.md#cancelScheduledPostcard) | **PUT** /v3/post/postcards/{message_id}/cancel | Cancel Scheduled Postcard |
| [**exportPostcardHistory()**](PostcardsApi.md#exportPostcardHistory) | **GET** /v3/post/postcards/history/export | Export Postcard History |
| [**sendPostcard()**](PostcardsApi.md#sendPostcard) | **POST** /v3/post/postcards/send | Send Postcard |
| [**viewPostcardHistory()**](PostcardsApi.md#viewPostcardHistory) | **GET** /v3/post/postcards/history | View Postcard History |


## `calculatePostcardPrice()`

```php
calculatePostcardPrice($content_type, $send_postcard_request): \ClickSend\Model\CalculatePostcardPrice
```

Calculate Postcard Price

_Calculate price for sending one or more postcards_  For `file_urls` field. You can attach at least 1 and max of 2 PDF file urls.  - Supply a single pdf with 2 pages (front and back) - Supply 2 urls to seperate PDFs       ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | file_urls | \\[string\\] | true | none | Postcard file URLs | | address_name | string | true | none | Name of address | | address_line_1 | string | true | none | First line of address | | address_line_2 | string | true | none | Second line of address | | address_city | string | true | none | City | | address_state | string | true | none | State | | address_postal_code | string | true | none | Postal code | | address_country | string | true | none | Country | | return_address_id | integer(int32) | true | none | ID of return address to use | | schedule | integer(int32) | false | none | When to send letter (0/null=now) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\PostcardsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_postcard_request = new \ClickSend\Model\SendPostcardRequest(); // \ClickSend\Model\SendPostcardRequest

try {
    $result = $apiInstance->calculatePostcardPrice($content_type, $send_postcard_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PostcardsApi->calculatePostcardPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_postcard_request** | [**\ClickSend\Model\SendPostcardRequest**](../Model/SendPostcardRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculatePostcardPrice**](../Model/CalculatePostcardPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelScheduledPostcard()`

```php
cancelScheduledPostcard($message_id): \ClickSend\Model\CancelScheduledPostcard
```

Cancel Scheduled Postcard

_Cancel scheduled postcard_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | message_id | query | string | true | Message ID of the scheduled postcard that is to be cancelled. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new ClickSend\Api\PostcardsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$message_id = 'message_id_example'; // string

try {
    $result = $apiInstance->cancelScheduledPostcard($message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PostcardsApi->cancelScheduledPostcard: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**|  | |

### Return type

[**\ClickSend\Model\CancelScheduledPostcard**](../Model/CancelScheduledPostcard.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportPostcardHistory()`

```php
exportPostcardHistory($content_type): \ClickSend\Model\ExportPostcardHistory
```

Export Postcard History

_Export postcard history to a CSV file_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | filename | query | string | true | Filename to export to |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\PostcardsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->exportPostcardHistory($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PostcardsApi->exportPostcardHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ExportPostcardHistory**](../Model/ExportPostcardHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendPostcard()`

```php
sendPostcard($content_type, $send_postcard_request): \ClickSend\Model\SendPostcard
```

Send Postcard

_Send one or more postcards_  ### **Supported File Types**  We support PDF, docx, doc, jpg, gif, png, and bmp. Contact us to add support for any other file type. If you're using docx, doc, jpg, gif, png, or bmp files, you'll need to convert the file first using our uploads endpoint with the querystring parameter ?convert=postcard. e.g. POST /uploads?convert=postcard. This will return a URL to the converted pdf file that can be used in the /post/postcards/send endpoint.  ### **Postcard Specification Guide**  Follow our [Postcard specification guide](https://help.clicksend.com/article/ysyql7bsr1-postcard-template) to ensure correct sending and postcard template information.  ### **Postcard File Options**  ### Use existing URL  With this option, you can use an existing URL to a `pdf` document. For example, you might generate the `pdf` on your server.  When using an existing url make sure that it is publicly accessible as it will not work if it is private.  For `file_urls` field. You can attach at least 1 and max of 2 PDF file urls.  - Supply a single pdf with 2 pages (front and back) - Supply 2 urls to seperate PDFs       ### Upload File to Our Server  With this option, you can use the [/uploads](/#upload-media-file) endpoint to upload the document. The `/uploads` endpoint returns a URL that can be used in the `/post/postcards/send` endpoint.  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | file_urls | \\[string\\] | true | none | Postcard file URLs | | address_name | string | true | none | Name of address | | address_line_1 | string | true | none | First line of address | | address_line_2 | string | true | none | Second line of address | | address_city | string | true | none | City | | address_state | string | true | none | State | | address_postal_code | string | true | none | Postal code | | address_country | string | true | none | Country | | return_address_id | integer(int32) | true | none | ID of return address to use | | schedule | integer(int32) | false | none | When to send letter (0/null=now) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\PostcardsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_postcard_request = new \ClickSend\Model\SendPostcardRequest(); // \ClickSend\Model\SendPostcardRequest

try {
    $result = $apiInstance->sendPostcard($content_type, $send_postcard_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PostcardsApi->sendPostcard: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_postcard_request** | [**\ClickSend\Model\SendPostcardRequest**](../Model/SendPostcardRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendPostcard**](../Model/SendPostcard.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewPostcardHistory()`

```php
viewPostcardHistory($content_type): \ClickSend\Model\ViewPostcardHistory
```

View Postcard History

_Retrieve the history of postcards sent or scheduled_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\PostcardsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewPostcardHistory($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling PostcardsApi->viewPostcardHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewPostcardHistory**](../Model/ViewPostcardHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
