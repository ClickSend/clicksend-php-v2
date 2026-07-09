# ClickSend\EmailToSmsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addAllowedEmail()**](EmailToSmsApi.md#addAllowedEmail) | **POST** /v3/sms/email-sms | Add Allowed Email |
| [**createStrippedStringRule()**](EmailToSmsApi.md#createStrippedStringRule) | **POST** /v3/sms/email-sms-stripped-strings | Create Stripped String Rule |
| [**deleteStrippedStringRule()**](EmailToSmsApi.md#deleteStrippedStringRule) | **DELETE** /v3/sms/email-sms-stripped-strings/{rule_id} | Delete Stripped String Rule |
| [**updateStrippedStringRule()**](EmailToSmsApi.md#updateStrippedStringRule) | **PUT** /v3/sms/email-sms-stripped-strings/{rule_id} | Update Stripped String Rule |
| [**viewAllowedEmails()**](EmailToSmsApi.md#viewAllowedEmails) | **GET** /v3/sms/email-sms | View Allowed Emails |
| [**viewStrippedStringRule()**](EmailToSmsApi.md#viewStrippedStringRule) | **GET** /v3/sms/email-sms-stripped-strings/{rule_id} | View Stripped String Rule |
| [**viewStrippedStringRules()**](EmailToSmsApi.md#viewStrippedStringRules) | **GET** /v3/sms/email-sms-stripped-strings | View Stripped String Rules |


## `addAllowedEmail()`

```php
addAllowedEmail($content_type, $add_allowed_email_request): \ClickSend\Model\AddAllowedEmail
```

Add Allowed Email

_Create email to sms allowed address_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | email_address | string | true | none | Your email address | | from | string | false | [yes](http://help.clicksend.com/SMS/what-is-a-sender-id-or-sender-number) | Your sender id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$add_allowed_email_request = new \ClickSend\Model\AddAllowedEmailRequest(); // \ClickSend\Model\AddAllowedEmailRequest

try {
    $result = $apiInstance->addAllowedEmail($content_type, $add_allowed_email_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->addAllowedEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **add_allowed_email_request** | [**\ClickSend\Model\AddAllowedEmailRequest**](../Model/AddAllowedEmailRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\AddAllowedEmail**](../Model/AddAllowedEmail.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createStrippedStringRule()`

```php
createStrippedStringRule($content_type, $create_stripped_string_rule_request): \ClickSend\Model\CreateStrippedStringRule
```

Create Stripped String Rule

_Create email to sms stripped string rule_  Create email to sms stripped string rules  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | stripped-string | body | string | true | String to be stripped. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_stripped_string_rule_request = new \ClickSend\Model\CreateStrippedStringRuleRequest(); // \ClickSend\Model\CreateStrippedStringRuleRequest

try {
    $result = $apiInstance->createStrippedStringRule($content_type, $create_stripped_string_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->createStrippedStringRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_stripped_string_rule_request** | [**\ClickSend\Model\CreateStrippedStringRuleRequest**](../Model/CreateStrippedStringRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateStrippedStringRule**](../Model/CreateStrippedStringRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteStrippedStringRule()`

```php
deleteStrippedStringRule($rule_id, $content_type): \ClickSend\Model\DeleteStrippedStringRule
```

Delete Stripped String Rule

_Delete email to sms stripped string rule_  Delete email to sms stripped string rule  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | rule_id | path | integer(int32) | true | Your rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$rule_id = 'rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteStrippedStringRule($rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->deleteStrippedStringRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteStrippedStringRule**](../Model/DeleteStrippedStringRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateStrippedStringRule()`

```php
updateStrippedStringRule($rule_id, $content_type, $create_stripped_string_rule_request): \ClickSend\Model\UpdateStrippedStringRule
```

Update Stripped String Rule

_Update email to sms stripped string rule_  Update email to sms stripped string rule  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | rule_id | path | integer(int32) | true | Your rule id | | stripped-string | body | string | true | String to be stripped. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$rule_id = 'rule_id_example'; // string
$content_type = application/json; // string
$create_stripped_string_rule_request = new \ClickSend\Model\CreateStrippedStringRuleRequest(); // \ClickSend\Model\CreateStrippedStringRuleRequest

try {
    $result = $apiInstance->updateStrippedStringRule($rule_id, $content_type, $create_stripped_string_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->updateStrippedStringRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **create_stripped_string_rule_request** | [**\ClickSend\Model\CreateStrippedStringRuleRequest**](../Model/CreateStrippedStringRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateStrippedStringRule**](../Model/UpdateStrippedStringRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAllowedEmails()`

```php
viewAllowedEmails($content_type): \ClickSend\Model\ViewAllowedEmails
```

View Allowed Emails

_Get list of email to sms allowed addresses_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAllowedEmails($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->viewAllowedEmails: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAllowedEmails**](../Model/ViewAllowedEmails.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewStrippedStringRule()`

```php
viewStrippedStringRule($rule_id, $content_type): \ClickSend\Model\ViewStrippedStringRule
```

View Stripped String Rule

_Get email to sms stripped string rule_  Get email to sms stripped string rule  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | rule_id | path | integer(int32) | true | Your rule id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$rule_id = 'rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewStrippedStringRule($rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->viewStrippedStringRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewStrippedStringRule**](../Model/ViewStrippedStringRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewStrippedStringRules()`

```php
viewStrippedStringRules($content_type): \ClickSend\Model\ViewStrippedStringRules
```

View Stripped String Rules

_Get list of email to sms stripped string rules_  Get list of email to sms stripped string rules  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailToSmsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewStrippedStringRules($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailToSmsApi->viewStrippedStringRules: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewStrippedStringRules**](../Model/ViewStrippedStringRules.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
