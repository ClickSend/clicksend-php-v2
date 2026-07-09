# ClickSend\OwnNumbersApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**deleteOwnNumber()**](OwnNumbersApi.md#deleteOwnNumber) | **DELETE** /v3/own-numbers/{own_number_id} | Delete Own Number |
| [**getOwnNumberDetail()**](OwnNumbersApi.md#getOwnNumberDetail) | **GET** /v3/own-numbers/{own_number_id} | Get Own Number Detail |
| [**listOwnNumbers()**](OwnNumbersApi.md#listOwnNumbers) | **GET** /v3/own-numbers | List Own Numbers |
| [**requestOwnNumberVerificationOtp()**](OwnNumbersApi.md#requestOwnNumberVerificationOtp) | **POST** /v3/own-numbers/verifications | Request Own Number Verification OTP |
| [**updateOwnNumber()**](OwnNumbersApi.md#updateOwnNumber) | **PATCH** /v3/own-numbers/{own_number_id} | Update Own Number |
| [**verifyOwnNumberOtp()**](OwnNumbersApi.md#verifyOwnNumberOtp) | **POST** /v3/own-numbers/verifications/{verification_id}/verify | Verify Own Number OTP |


## `deleteOwnNumber()`

```php
deleteOwnNumber($own_number_id, $content_type): \ClickSend\Model\OwnNumber
```

Delete Own Number

_Delete a specific own numbers._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | own_number_id | path | uuid | true | ID of the own number |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\OwnNumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$own_number_id = 'own_number_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteOwnNumber($own_number_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OwnNumbersApi->deleteOwnNumber: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **own_number_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\OwnNumber**](../Model/OwnNumber.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getOwnNumberDetail()`

```php
getOwnNumberDetail($own_number_id, $content_type): \ClickSend\Model\OwnNumber
```

Get Own Number Detail

_Get a specific own numbers._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | own_number_id | path | uuid | true | ID of the own number |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\OwnNumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$own_number_id = 'own_number_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->getOwnNumberDetail($own_number_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OwnNumbersApi->getOwnNumberDetail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **own_number_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\OwnNumber**](../Model/OwnNumber.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listOwnNumbers()`

```php
listOwnNumbers($content_type): \ClickSend\Model\ListOwnNumbers
```

List Own Numbers

_List own numbers._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | offset | query | uuid | false | Page(offset) to be used for pagination. Example: `offset=f99872cc-11a6-48ba-a9f2-bcfb6dd1e3d4#8fa5ebc2-777b-45db-a448-ec76a40d4384` | | page_size | query | integer | false | Number of records per page. Default: 10. Range \\[1..500\\] | | filter\\[status\\]\\[\\] | query | string | false | Filter by statuses. Value must be in enum \\[`PENDING`, `APPROVED`, `REJECTED`\\]. For example: `filter[status][0]=PENDING&filter[status][1]=APPROVED` . | | sort_by | query | string | false | Sort by parameter. Default: `created_timestamp` | | sort_direction | query | string | false | Direction of sorting. Default: `asc`. Value must be in enum \\[`asc`, `desc`\\]. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\OwnNumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->listOwnNumbers($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OwnNumbersApi->listOwnNumbers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ListOwnNumbers**](../Model/ListOwnNumbers.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestOwnNumberVerificationOtp()`

```php
requestOwnNumberVerificationOtp($content_type, $request_own_number_verification_otp_request): \ClickSend\Model\RequestOwnNumberVerificationOtp
```

Request Own Number Verification OTP

_Request to generate own number verification OTP_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | label | string | false | none | Custom label for phone number. Length must be between 1 - 200 characters. | | phone_number | string | true | none | Phone number. | | country | string | false | none | Country code. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\OwnNumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$request_own_number_verification_otp_request = new \ClickSend\Model\RequestOwnNumberVerificationOtpRequest(); // \ClickSend\Model\RequestOwnNumberVerificationOtpRequest

try {
    $result = $apiInstance->requestOwnNumberVerificationOtp($content_type, $request_own_number_verification_otp_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OwnNumbersApi->requestOwnNumberVerificationOtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **request_own_number_verification_otp_request** | [**\ClickSend\Model\RequestOwnNumberVerificationOtpRequest**](../Model/RequestOwnNumberVerificationOtpRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\RequestOwnNumberVerificationOtp**](../Model/RequestOwnNumberVerificationOtp.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateOwnNumber()`

```php
updateOwnNumber($own_number_id): \ClickSend\Model\OwnNumber
```

Update Own Number

_Update details of a specific own numbers._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | own_number_id | path | uuid | true | ID of the own number |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | label | string | false | none | Custom label for phone number. Length must be between 1 - 200 characters. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new ClickSend\Api\OwnNumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$own_number_id = 'own_number_id_example'; // string

try {
    $result = $apiInstance->updateOwnNumber($own_number_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OwnNumbersApi->updateOwnNumber: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **own_number_id** | **string**|  | |

### Return type

[**\ClickSend\Model\OwnNumber**](../Model/OwnNumber.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyOwnNumberOtp()`

```php
verifyOwnNumberOtp($verification_id, $content_type, $verify_own_number_otp_request): \ClickSend\Model\VerifyOwnNumberOtp
```

Verify Own Number OTP

_Request to verify an OTP for Own Number verification_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | verification_id | path | uuid | true | ID of the Own Number verification |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | code | string | true | none | OTP code. Length must be 6 characters | | phone_number | string | true | none | Phone number. | | country | string | false | none | Country code. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\OwnNumbersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$verification_id = 'verification_id_example'; // string
$content_type = application/json; // string
$verify_own_number_otp_request = new \ClickSend\Model\VerifyOwnNumberOtpRequest(); // \ClickSend\Model\VerifyOwnNumberOtpRequest

try {
    $result = $apiInstance->verifyOwnNumberOtp($verification_id, $content_type, $verify_own_number_otp_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling OwnNumbersApi->verifyOwnNumberOtp: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **verification_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **verify_own_number_otp_request** | [**\ClickSend\Model\VerifyOwnNumberOtpRequest**](../Model/VerifyOwnNumberOtpRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\VerifyOwnNumberOtp**](../Model/VerifyOwnNumberOtp.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
