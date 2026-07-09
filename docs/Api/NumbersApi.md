# ClickSend\NumbersApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**purchaseDedicatedNumber()**](NumbersApi.md#purchaseDedicatedNumber) | **POST** /v3/numbers/buy/{dedicated_number} | Purchase Dedicated Number |
| [**registerNumbers()**](NumbersApi.md#registerNumbers) | **POST** /v3/numbers/registrations/number-types/{number_type}/country/{country_code} | Register Numbers |
| [**viewAvailableNumbers()**](NumbersApi.md#viewAvailableNumbers) | **GET** /v3/numbers/search/{country} | View Available Numbers |
| [**viewYourNumbers()**](NumbersApi.md#viewYourNumbers) | **GET** /v3/numbers | View Your Numbers |


## `purchaseDedicatedNumber()`

```php
purchaseDedicatedNumber($dedicated_number, $buy_number_request, $content_type, $type): \ClickSend\Model\PurchaseDedicatedNumber
```

Purchase Dedicated Number

_Buy dedicated number_  This endpoint allows you to purchase a dedicated phone number for messaging services. You can optionally include registration data for compliance purposes.  ### Request Body  | Field | Type | Required | Description | | --- | --- | --- | --- | | dedicated_number | string | true | Phone number to purchase | | type | string | true | Service type (sms, mms) | | registration_data | object | false | Registration data for compliance (AU SMS/MMS numbers only) |  #### Registration Data Fields (Optional)  | Field | Type | Required | Description | | --- | --- | --- | --- | | business_name | string | true | Name of the business (2 - 100 characters) | | business_address | string | true | Business address (5 - 150 characters) | | suburb | string | true | Suburb/City (2 - 50 characters) | | postcode | string | true | Postal code (2 - 20 characters) | | state | string | true | State/Province (2 - 50 characters) | | contact_name | string | true | Contact person name (2 - 100 characters) | | contact_number | string | true | Contact phone number (valid local or international phone number) | | country | string | true | Country code (ISO 3166-1 alpha-2) |   ### Path Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | dedicated_number | path | string | true | Phone number to purchase |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\NumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$dedicated_number = +614197651956; // string | Phone number to purchase
$buy_number_request = new \ClickSend\Model\BuyNumberRequest(); // \ClickSend\Model\BuyNumberRequest
$content_type = application/json; // string
$type = sms; // string

try {
    $result = $apiInstance->purchaseDedicatedNumber($dedicated_number, $buy_number_request, $content_type, $type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling NumbersApi->purchaseDedicatedNumber: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **dedicated_number** | **string**| Phone number to purchase | |
| **buy_number_request** | [**\ClickSend\Model\BuyNumberRequest**](../Model/BuyNumberRequest.md)|  | |
| **content_type** | **string**|  | [optional] |
| **type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\PurchaseDedicatedNumber**](../Model/PurchaseDedicatedNumber.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `registerNumbers()`

```php
registerNumbers($number_type, $country_code, $content_type, $register_numbers_request): \ClickSend\Model\RegisterNumbers
```

Register Numbers

<div style=\"background-color: #e8f4ff; padding: 15px; border-radius: 4px; border-left: 4px solid #0066cc;\"> This endpoint is currently only available for <b>Canada 10DLC</b> number registration. </div>  Registers a number that requires additional verification information. This endpoint facilitates the registration process for numbers requiring special compliance documentation.  After submission, ClickSend's compliance team will review the registration and notify you of the approval status.  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses. <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\NumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$number_type = 10dlc; // string | The type of number being registered
$country_code = US, CA; // string | Two-character ISO country code
$content_type = application/json; // string
$register_numbers_request = new \ClickSend\Model\RegisterNumbersRequest(); // \ClickSend\Model\RegisterNumbersRequest

try {
    $result = $apiInstance->registerNumbers($number_type, $country_code, $content_type, $register_numbers_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling NumbersApi->registerNumbers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **number_type** | **string**| The type of number being registered | |
| **country_code** | **string**| Two-character ISO country code | |
| **content_type** | **string**|  | [optional] |
| **register_numbers_request** | [**\ClickSend\Model\RegisterNumbersRequest**](../Model/RegisterNumbersRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\RegisterNumbers**](../Model/RegisterNumbers.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAvailableNumbers()`

```php
viewAvailableNumbers($country, $content_type): \ClickSend\Model\ViewAvailableNumbers
```

View Available Numbers

_Get all dedicated numbers by country_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | country | path | string | true | Country code to search | | search | query | string | false | Your search pattern or query. | | search_type | query | integer(int32) | false | Your strategy for searching, 0 = starts with, 1 = anywhere, 2 = ends with. | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\NumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$country = 'country_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAvailableNumbers($country, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling NumbersApi->viewAvailableNumbers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **country** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAvailableNumbers**](../Model/ViewAvailableNumbers.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewYourNumbers()`

```php
viewYourNumbers($content_type, $page, $limit, $q, $q2, $excluding_number_type, $exclude_10dlc_campaign): \ClickSend\Model\ViewYourNumbers
```

View Your Numbers

_Get all available dedicated numbers_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) | | q | query | string | false | Filter numbers based on multiple criteria. The query string should be formatted as key-value pairs separated by commas. Available filter keys: `type`, `number_type`, `country` | | q2 | query | string | false | Filter numbers based on multiple criteria. The query string should be formatted as key-value pairs separated by commas. Available filter keys: `type` | | excluding_number_type | query | string | false | Exclude specific number types from the results. Available number types: `shortcode`, `tollfree`, `10DLC` | | exclude_10dlc_campaign | query | boolean | false | When set to true, excludes all numbers that are associated with 10DLC campaigns |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\NumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$page = 1; // int | Page number
$limit = 100; // int | Number of records per page
$q = type:sms,number_type:longcode,country:AU; // string | Filter numbers based on multiple criteria. The query string should be formatted as key-value pairs separated by commas. Available filter keys: - `type`: Message type (e.g., `SMS`, `MMS`) - `number_type`: Number classification (e.g., `longcode`, `shortcode`, `tollfree`, `10DLC`) - `country`: Two-letter country code (e.g., `AU`, `US`)
$q2 = type:mms; // string
$excluding_number_type = 10DLC; // string | Exclude specific number types from the results. Available number types: - `shortcode` - `tollfree` - `10DLC`
$exclude_10dlc_campaign = true; // bool | When set to true, excludes all numbers that are associated with 10DLC campaigns

try {
    $result = $apiInstance->viewYourNumbers($content_type, $page, $limit, $q, $q2, $excluding_number_type, $exclude_10dlc_campaign);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling NumbersApi->viewYourNumbers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **page** | **int**| Page number | [optional] [default to 1] |
| **limit** | **int**| Number of records per page | [optional] [default to 15] |
| **q** | **string**| Filter numbers based on multiple criteria. The query string should be formatted as key-value pairs separated by commas. Available filter keys: - &#x60;type&#x60;: Message type (e.g., &#x60;SMS&#x60;, &#x60;MMS&#x60;) - &#x60;number_type&#x60;: Number classification (e.g., &#x60;longcode&#x60;, &#x60;shortcode&#x60;, &#x60;tollfree&#x60;, &#x60;10DLC&#x60;) - &#x60;country&#x60;: Two-letter country code (e.g., &#x60;AU&#x60;, &#x60;US&#x60;) | [optional] |
| **q2** | **string**|  | [optional] |
| **excluding_number_type** | **string**| Exclude specific number types from the results. Available number types: - &#x60;shortcode&#x60; - &#x60;tollfree&#x60; - &#x60;10DLC&#x60; | [optional] |
| **exclude_10dlc_campaign** | **bool**| When set to true, excludes all numbers that are associated with 10DLC campaigns | [optional] [default to false] |

### Return type

[**\ClickSend\Model\ViewYourNumbers**](../Model/ViewYourNumbers.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
