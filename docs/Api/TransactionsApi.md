# ClickSend\TransactionsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**currentPaymentInfo()**](TransactionsApi.md#currentPaymentInfo) | **GET** /v3/recharge/credit-card | Current Payment Info |
| [**purchaseRechargePackage()**](TransactionsApi.md#purchaseRechargePackage) | **PUT** /v3/recharge/purchase/{package_id} | Purchase Recharge Package |
| [**updatePaymentInfo()**](TransactionsApi.md#updatePaymentInfo) | **PUT** /v3/recharge/credit-card | Update Payment Info |
| [**viewAllTransactions()**](TransactionsApi.md#viewAllTransactions) | **GET** /v3/recharge/transactions | View All Transactions |
| [**viewRechargePackages()**](TransactionsApi.md#viewRechargePackages) | **GET** /v3/recharge/packages | View Recharge Packages |
| [**viewSpecificTransaction()**](TransactionsApi.md#viewSpecificTransaction) | **GET** /v3/recharge/transactions/{transaction_id} | View Specific Transaction |


## `currentPaymentInfo()`

```php
currentPaymentInfo($content_type): \ClickSend\Model\CurrentPaymentInfo
```

Current Payment Info

_Get current payment info_  This endpoint returns your current payment info, we do not store credit card numbers, only a card token for security reasons.  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\TransactionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->currentPaymentInfo($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TransactionsApi->currentPaymentInfo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\CurrentPaymentInfo**](../Model/CurrentPaymentInfo.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `purchaseRechargePackage()`

```php
purchaseRechargePackage($package_id, $content_type): \ClickSend\Model\PurchaseRechargePackage
```

Purchase Recharge Package

_Purchase a package_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | package_id | path | integer(int32) | true | ID of package to purchase |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\TransactionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$package_id = 'package_id_example'; // string
$content_type = application/x-www-form-urlencoded; // string

try {
    $result = $apiInstance->purchaseRechargePackage($package_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TransactionsApi->purchaseRechargePackage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **package_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\PurchaseRechargePackage**](../Model/PurchaseRechargePackage.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updatePaymentInfo()`

```php
updatePaymentInfo($content_type, $update_payment_info_request): \ClickSend\Model\UpdatePaymentInfo
```

Update Payment Info

_Update credit card info_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | number | string | true | none | Credit card number | | expiry_month | integer(int32) | true | none | Expiry month of credit card | | expiry_year | integer(int32) | true | none | Expiry year of credit card | | cvc | integer(int32) | true | none | CVC number of credit card | | name | string | true | none | Name printed on credit card | | bank_name | string | true | none | Name of bank that credit card belongs to |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\TransactionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/x-www-form-urlencoded; // string
$update_payment_info_request = new \ClickSend\Model\UpdatePaymentInfoRequest(); // \ClickSend\Model\UpdatePaymentInfoRequest

try {
    $result = $apiInstance->updatePaymentInfo($content_type, $update_payment_info_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TransactionsApi->updatePaymentInfo: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **update_payment_info_request** | [**\ClickSend\Model\UpdatePaymentInfoRequest**](../Model/UpdatePaymentInfoRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdatePaymentInfo**](../Model/UpdatePaymentInfo.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAllTransactions()`

```php
viewAllTransactions($content_type): \ClickSend\Model\ViewAllTransactions
```

View All Transactions

_Purchase a package_  Get all transactions  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\TransactionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAllTransactions($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TransactionsApi->viewAllTransactions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAllTransactions**](../Model/ViewAllTransactions.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewRechargePackages()`

```php
viewRechargePackages($content_type): \ClickSend\Model\ViewRechargePackages
```

View Recharge Packages

_Get list of all packages_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | country | query | string | false | Two-letter country code ([ISO3166](https://en.wikipedia.org/wiki/ISO_3166)) |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\TransactionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewRechargePackages($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TransactionsApi->viewRechargePackages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewRechargePackages**](../Model/ViewRechargePackages.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewSpecificTransaction()`

```php
viewSpecificTransaction($transaction_id, $content_type): \ClickSend\Model\ViewSpecificTransaction
```

View Specific Transaction

_Get specific Transaction_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | transaction_id | path | string | true | ID of transaction to retrieve |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\TransactionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$transaction_id = 'transaction_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewSpecificTransaction($transaction_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TransactionsApi->viewSpecificTransaction: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **transaction_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewSpecificTransaction**](../Model/ViewSpecificTransaction.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
