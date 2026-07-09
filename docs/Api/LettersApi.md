# ClickSend\LettersApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculateLetterPrice()**](LettersApi.md#calculateLetterPrice) | **POST** /v3/post/letters/price | Calculate Letter Price |
| [**cancelScheduledLetter()**](LettersApi.md#cancelScheduledLetter) | **PUT** /v3/post/letters/{message_id}/cancel | Cancel Scheduled Letter |
| [**detectAddress()**](LettersApi.md#detectAddress) | **POST** /v3/post/letters/detect-address | Detect Address |
| [**exportLetterHistory()**](LettersApi.md#exportLetterHistory) | **GET** /v3/post/letters/history/export | Export Letter History |
| [**sendLetter()**](LettersApi.md#sendLetter) | **POST** /v3/post/letters/send | Send Letter |
| [**viewLetterHistory()**](LettersApi.md#viewLetterHistory) | **GET** /v3/post/letters/history | View Letter History |


## `calculateLetterPrice()`

```php
calculateLetterPrice($content_type, $calculate_letter_price_request): \ClickSend\Model\CalculateLetterPrice
```

Calculate Letter Price

_Calculate letter price_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | file_url | string | true | none | URL of file to send | | address_name | string | true | none | Name of address | | address_line_1 | string | true | none | First line of address | | address_line_2 | string | true | none | Second line of address | | address_city | string | true | none | City | | address_state | string | true | none | State | | address_postal_code | string | true | none | Postal code | | address_country | string | true | none | Country | | return_address_id | integer(int32) | true | none | ID of return address to use | | schedule | integer(int32) | false | none | When to send letter (0/null=now) | | template_used | integer(int1) | false | none | Whether using our letter template. Flag value must be 1 for yes or 0 for no. | | duplex | integer(int1) | false | none | Whether letter is duplex. Flag value must be 1 for yes or 0 for no. | | colour | integer(int1) | false | none | Whether letter is in colour. Flag value must be 1 for yes or 0 for no. | | priority_post | integer(int1) | false | none | Whether letter is priority. Flag value must be 1 for yes or 0 for no. | | source | string | false | none | Source being sent from |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$calculate_letter_price_request = new \ClickSend\Model\CalculateLetterPriceRequest(); // \ClickSend\Model\CalculateLetterPriceRequest

try {
    $result = $apiInstance->calculateLetterPrice($content_type, $calculate_letter_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->calculateLetterPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **calculate_letter_price_request** | [**\ClickSend\Model\CalculateLetterPriceRequest**](../Model/CalculateLetterPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateLetterPrice**](../Model/CalculateLetterPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelScheduledLetter()`

```php
cancelScheduledLetter($message_id): \ClickSend\Model\CancelScheduledLetter
```

Cancel Scheduled Letter

_Cancel scheduled letter_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | message_id | query | string | true | Message ID of the scheduled letter that is to be cancelled. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new ClickSend\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$message_id = 'message_id_example'; // string

try {
    $result = $apiInstance->cancelScheduledLetter($message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->cancelScheduledLetter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**|  | |

### Return type

[**\ClickSend\Model\CancelScheduledLetter**](../Model/CancelScheduledLetter.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `detectAddress()`

```php
detectAddress($content_type, $body): \ClickSend\Model\DetectAddress
```

Detect Address

_Detects address in uploaded file._  The `detect-address` endpoint accepts either a letter in PDF format or an address string and attempts to convert it to a standard address format. Note that the PDF should be in standard address format, having the recipient's name and address listed at the top.  The endpoint accepts two types of data: 1. A PDF file in `base64` encoding. In this case, submit the `base64`\\-encoded PDF file contents in the `content` field of the request body. 2. An address string. In this case, submit the address in a string using the `address` field of the request body.  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | convert | query | string | true | none | | content | body | string | true | Base64-encoded file contents |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$body = array('key' => new \stdClass); // object

try {
    $result = $apiInstance->detectAddress($content_type, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->detectAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **body** | **object**|  | [optional] |

### Return type

[**\ClickSend\Model\DetectAddress**](../Model/DetectAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportLetterHistory()`

```php
exportLetterHistory($content_type, $filename, $q, $order_by, $date_from, $date_to, $limit): \ClickSend\Model\ExportLetterHistory
```

Export Letter History

_export letter history_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | filename | query | string | true | Filename to export to |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$filename = Post_history.csv; // string
$q = 'q_example'; // string
$order_by = date_added:desc; // string
$date_from = 'date_from_example'; // string
$date_to = 'date_to_example'; // string
$limit = 50000; // int

try {
    $result = $apiInstance->exportLetterHistory($content_type, $filename, $q, $order_by, $date_from, $date_to, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->exportLetterHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **filename** | **string**|  | [optional] |
| **q** | **string**|  | [optional] |
| **order_by** | **string**|  | [optional] |
| **date_from** | **string**|  | [optional] |
| **date_to** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] |

### Return type

[**\ClickSend\Model\ExportLetterHistory**](../Model/ExportLetterHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendLetter()`

```php
sendLetter($content_type, $send_letter_request): \ClickSend\Model\SendLetter
```

Send Letter

### Send letter  ### **Supported File Types**  We support `pdf`, `docx` and `doc` files. Contact us to add support for any other file type. If you're using `docx` or `doc` files, you'll need to convert the file first using our uploads endpoint with the querystring parameter `convert=post` e.g. `POST https://rest.clicksend.com/v3/uploads?convert=post`. This will return a URL to the converted pdf file that can be used in the `/post/letters/send` endpoint.  ### **Letter Specification Guide**  Follow our [Letter specification guide](https://help.clicksend.com/article/wcpkkoou6c-post-letter-template) to ensure correct sending and letter template information.  ### **Letter File Options**  ### Use existing URL  With this option, you can use an existing URL to a `pdf` document. For example, you might generate the `pdf` on your server.  When using an existing url make sure that it is publicly accessible as it will not work if it is private.  ### Upload File to Our Server  With this option, you can use the [/uploads](/#upload-media-file) endpoint to upload the document. The `/uploads` endpoint returns a URL that can be used in the `/post/letters/send` endpoint.  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | file_url | string | true | none | URL of file to send | | address_name | string | true | none | Name of address | | address_line_1 | string | true | none | First line of address | | address_line_2 | string | true | none | Second line of address | | address_city | string | true | none | City | | address_state | string | true | none | State | | address_postal_code | string | true | none | Postal code | | address_country | string | true | none | Country | | return_address_id | integer(int32) | true | none | ID of return address to use | | schedule | integer(int32) | false | none | When to send letter (0/null=now) | | template_used | integer(int1) | false | none | Whether using our letter template. Flag value must be 1 for yes or 0 for no. | | duplex | integer(int1) | false | none | Whether letter is duplex. Flag value must be 1 for yes or 0 for no. | | colour | integer(int1) | false | none | Whether letter is in colour. Flag value must be 1 for yes or 0 for no. | | priority_post | integer(int1) | false | none | Whether letter is priority, Flag value must be 1 for yes or 0 for no. | | source | string | false | none | Source being sent from |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_letter_request = new \ClickSend\Model\SendLetterRequest(); // \ClickSend\Model\SendLetterRequest

try {
    $result = $apiInstance->sendLetter($content_type, $send_letter_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->sendLetter: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_letter_request** | [**\ClickSend\Model\SendLetterRequest**](../Model/SendLetterRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendLetter**](../Model/SendLetter.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewLetterHistory()`

```php
viewLetterHistory($content_type): \ClickSend\Model\ViewLetterHistory
```

View Letter History

_Get all letter history_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\LettersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewLetterHistory($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling LettersApi->viewLetterHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewLetterHistory**](../Model/ViewLetterHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
