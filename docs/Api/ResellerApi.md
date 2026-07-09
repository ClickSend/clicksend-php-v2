# ClickSend\ResellerApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createResellerAccount()**](ResellerApi.md#createResellerAccount) | **POST** /v3/reseller/accounts | Create Reseller Account |
| [**resellerTransferCredit()**](ResellerApi.md#resellerTransferCredit) | **PUT** /v3/reseller/transfer-credit | Reseller Transfer Credit |
| [**updateClientAccount()**](ResellerApi.md#updateClientAccount) | **PUT** /v3/reseller/accounts/{client_user_id} | Update Client Account |
| [**viewClientAccounts()**](ResellerApi.md#viewClientAccounts) | **GET** /v3/reseller/accounts | View Client Accounts |
| [**viewSpecificClientAccount()**](ResellerApi.md#viewSpecificClientAccount) | **GET** /v3/reseller/accounts/{client_user_id} | View Specific Client Account |


## `createResellerAccount()`

```php
createResellerAccount($content_type, $create_reseller_account_request): \ClickSend\Model\CreateResellerAccount
```

Create Reseller Account

_Create reseller account_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | username | string | true | none | Account username | | password | string | true | none | Account password (unhashed) | | user_email | string | true | none | Account email | | user_phone | string | true | none | Account phone number | | user_first_name | string | true | none | Account owner first name | | user_last_name | string | true | none | Account owner last name | | account_name | string | true | none | Account name (usually company name) | | country | string | true | none | Country of account holder |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ResellerApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_reseller_account_request = new \ClickSend\Model\CreateResellerAccountRequest(); // \ClickSend\Model\CreateResellerAccountRequest

try {
    $result = $apiInstance->createResellerAccount($content_type, $create_reseller_account_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ResellerApi->createResellerAccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_reseller_account_request** | [**\ClickSend\Model\CreateResellerAccountRequest**](../Model/CreateResellerAccountRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateResellerAccount**](../Model/CreateResellerAccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `resellerTransferCredit()`

```php
resellerTransferCredit($content_type, $update_payment_info_request): \ClickSend\Model\ResellerTransferCredit
```

Reseller Transfer Credit

_Transfer Credit_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | client_user_id | integer(int32) | true | none | User ID of client | | balance | integer(int32) | true | none | Balance to transfer | | currency | string | true | none | Currency of balance to transfer |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ResellerApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/x-www-form-urlencoded; // string
$update_payment_info_request = new \ClickSend\Model\UpdatePaymentInfoRequest(); // \ClickSend\Model\UpdatePaymentInfoRequest

try {
    $result = $apiInstance->resellerTransferCredit($content_type, $update_payment_info_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ResellerApi->resellerTransferCredit: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **update_payment_info_request** | [**\ClickSend\Model\UpdatePaymentInfoRequest**](../Model/UpdatePaymentInfoRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\ResellerTransferCredit**](../Model/ResellerTransferCredit.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateClientAccount()`

```php
updateClientAccount($client_user_id, $content_type, $update_payment_info_request): \ClickSend\Model\UpdateClientAccount
```

Update Client Account

_Update Reseller clients Account_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | client_user_id | path | integer(int32) | true | User ID of client |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | username | string | true | none | Account username | | password | string | true | none | Account password (unhashed) | | user_email | string | true | none | Account email | | user_phone | string | true | none | Account phone number | | user_first_name | string | true | none | Account owner first name | | user_last_name | string | true | none | Account owner last name | | account_name | string | true | none | Account name (usually company name) | | country | string | true | none | Country of account holder |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ResellerApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$client_user_id = 'client_user_id_example'; // string
$content_type = application/x-www-form-urlencoded; // string
$update_payment_info_request = new \ClickSend\Model\UpdatePaymentInfoRequest(); // \ClickSend\Model\UpdatePaymentInfoRequest

try {
    $result = $apiInstance->updateClientAccount($client_user_id, $content_type, $update_payment_info_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ResellerApi->updateClientAccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **client_user_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_payment_info_request** | [**\ClickSend\Model\UpdatePaymentInfoRequest**](../Model/UpdatePaymentInfoRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateClientAccount**](../Model/UpdateClientAccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewClientAccounts()`

```php
viewClientAccounts($content_type): \ClickSend\Model\ViewClientAccounts
```

View Client Accounts

_Get list of reseller accounts_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ResellerApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewClientAccounts($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ResellerApi->viewClientAccounts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewClientAccounts**](../Model/ViewClientAccounts.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSpecificClientAccount()`

```php
viewSpecificClientAccount($client_user_id, $content_type): \ClickSend\Model\ViewSpecificClientAccount
```

View Specific Client Account

_Get Reseller clients Account_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | client_user_id | path | integer(int32) | true | User ID of client |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\ResellerApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$client_user_id = 'client_user_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSpecificClientAccount($client_user_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ResellerApi->viewSpecificClientAccount: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **client_user_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSpecificClientAccount**](../Model/ViewSpecificClientAccount.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
