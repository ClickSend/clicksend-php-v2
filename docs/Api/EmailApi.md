# ClickSend\EmailApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculateEmailCampaignPrice()**](EmailApi.md#calculateEmailCampaignPrice) | **POST** /v3/email-campaigns/price | Calculate Email Campaign Price |
| [**calculateEmailPrice()**](EmailApi.md#calculateEmailPrice) | **POST** /v3/email/price | Calculate Email Price |
| [**cancelEmailCampaign()**](EmailApi.md#cancelEmailCampaign) | **PUT** /v3/email-campaigns/{email_campaign_id}/cancel | Cancel Email Campaign |
| [**createAllowedEmailAddress()**](EmailApi.md#createAllowedEmailAddress) | **POST** /v3/email/addresses | Create Allowed Email Address |
| [**createEmailDeliveryReceiptRule()**](EmailApi.md#createEmailDeliveryReceiptRule) | **POST** /v3/automations/email/receipts | Create Email Delivery Receipt Rule |
| [**createEmailTemplate()**](EmailApi.md#createEmailTemplate) | **POST** /v3/email/templates | Create Email Template |
| [**deleteAllowedEmailAddress()**](EmailApi.md#deleteAllowedEmailAddress) | **DELETE** /v3/email/addresses/{email_address_id} | Delete Allowed Email Address |
| [**deleteEmailDeliveryReceiptRule()**](EmailApi.md#deleteEmailDeliveryReceiptRule) | **DELETE** /v3/automations/email/receipts/{receipt_rule_id} | Delete Email Delivery Receipt Rule |
| [**deleteEmailTemplate()**](EmailApi.md#deleteEmailTemplate) | **DELETE** /v3/email/templates/{template_id} | Delete Email Template |
| [**exportEmailCampaignHistory()**](EmailApi.md#exportEmailCampaignHistory) | **GET** /v3/email-campaigns/{email_campaign_id}/history/export | Export Email Campaign History |
| [**exportEmailHistory()**](EmailApi.md#exportEmailHistory) | **GET** /v3/email/history/export | Export Email History |
| [**sendEmail()**](EmailApi.md#sendEmail) | **POST** /v3/email/send | Send Email |
| [**sendEmailCampaign()**](EmailApi.md#sendEmailCampaign) | **POST** /v3/email-campaigns/send | Send Email Campaign |
| [**sendEmailVerificationToken()**](EmailApi.md#sendEmailVerificationToken) | **PUT** /v3/email/address-verify/{email_address_id}/send | Send Email Verification Token |
| [**updateEmailCampaign()**](EmailApi.md#updateEmailCampaign) | **PUT** /v3/email-campaigns/{email_campaign_id} | Update Email Campaign |
| [**updateEmailDeliveryReceiptRule()**](EmailApi.md#updateEmailDeliveryReceiptRule) | **PUT** /v3/automations/email/receipts/{receipt_rule_id} | Update Email Delivery Receipt Rule |
| [**updateEmailTemplate()**](EmailApi.md#updateEmailTemplate) | **PUT** /v3/email/templates/{template_id} | Update Email Template |
| [**verifyAllowedEmailAddress()**](EmailApi.md#verifyAllowedEmailAddress) | **PUT** /v3/email/address-verify/{email_address_id}/verify/{activation_token} | Verify Allowed Email Address |
| [**viewAllEmailCampaigns()**](EmailApi.md#viewAllEmailCampaigns) | **GET** /v3/email-campaigns | View All Email Campaigns |
| [**viewAllowedEmailAddress()**](EmailApi.md#viewAllowedEmailAddress) | **GET** /v3/email/addresses/{email_address_id} | View Allowed Email Address |
| [**viewAllowedEmailAddresses()**](EmailApi.md#viewAllowedEmailAddresses) | **GET** /v3/email/addresses | View Allowed Email Addresses |
| [**viewEmailCampaign()**](EmailApi.md#viewEmailCampaign) | **GET** /v3/email-campaigns/{email_campaign_id} | View Email Campaign |
| [**viewEmailCampaignHistory()**](EmailApi.md#viewEmailCampaignHistory) | **GET** /v3/email-campaigns/{email_campaign_id}/history | View Email Campaign History |
| [**viewEmailDeliveryReceiptRule()**](EmailApi.md#viewEmailDeliveryReceiptRule) | **GET** /v3/automations/email/receipts/{receipt_rule_id} | View Email Delivery Receipt Rule |
| [**viewEmailDeliveryReceiptRules()**](EmailApi.md#viewEmailDeliveryReceiptRules) | **GET** /v3/automations/email/receipts | View Email Delivery Receipt Rules |
| [**viewEmailHistory()**](EmailApi.md#viewEmailHistory) | **GET** /v3/email/history | View Email History |
| [**viewEmailTemplate()**](EmailApi.md#viewEmailTemplate) | **GET** /v3/email/templates/{template_id} | View Email Template |
| [**viewEmailTemplates()**](EmailApi.md#viewEmailTemplates) | **GET** /v3/email/templates | View Email Templates |
| [**viewMasterEmailTemplate()**](EmailApi.md#viewMasterEmailTemplate) | **GET** /v3/email/master-templates/{template_id} | View Master Email Template |
| [**viewMasterEmailTemplates()**](EmailApi.md#viewMasterEmailTemplates) | **GET** /v3/email/master-templates | View Master Email Templates |
| [**viewTemplateCategories()**](EmailApi.md#viewTemplateCategories) | **GET** /v3/email/master-templates-categories | View Template Categories |
| [**viewTemplateCategory()**](EmailApi.md#viewTemplateCategory) | **GET** /v3/email/master-templates-categories/{category_id} | View Template Category |
| [**viewTemplatesInCategory()**](EmailApi.md#viewTemplatesInCategory) | **GET** /v3/email/master-templates-categories/{category_id}/master-templates | View Templates in Category |


## `calculateEmailCampaignPrice()`

```php
calculateEmailCampaignPrice($content_type, $calculate_email_campaign_price_request): \ClickSend\Model\CalculateEmailCampaignPrice
```

Calculate Email Campaign Price

_Calculate email campaign price_  Calculate email campaign price  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | name | string | true | none | Your campaign name. | | subject | string | true | none | Your campaign subject. | | body | string | true | none | Your campaign message. | | from_email_address_id | number | true | none | The allowed email address id. | | from_name | string | true | none | Your name or business name. | | template_id | number | false | none | Your template id. | | list_id | number | true | none | Your contact list id. | | schedule | integer(int32) | false | none | Your schedule timestamp. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$calculate_email_campaign_price_request = new \ClickSend\Model\CalculateEmailCampaignPriceRequest(); // \ClickSend\Model\CalculateEmailCampaignPriceRequest

try {
    $result = $apiInstance->calculateEmailCampaignPrice($content_type, $calculate_email_campaign_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->calculateEmailCampaignPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **calculate_email_campaign_price_request** | [**\ClickSend\Model\CalculateEmailCampaignPriceRequest**](../Model/CalculateEmailCampaignPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateEmailCampaignPrice**](../Model/CalculateEmailCampaignPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `calculateEmailPrice()`

```php
calculateEmailPrice($content_type, $calculate_email_price_request): \ClickSend\Model\CalculateEmailPrice
```

Calculate Email Price

_Get transactional email price_  Get transactional email price  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | to | array | true | none | Array of To Recipient items. (array of names and emails) | | cc | array | false | none | Array of Cc Recipient items. (array of names and emails) | | bcc | array | false | none | Array of Bcc Recipient items. (array of names and emails) | | from | object | true | none | From Email object. (object containing name and email) | | body | string | true | none | Body of the email. | | attachments | array | false | none | Array of Attachment items. | | schedule | number | false | none | Schedule. | | name | string | false | none | Name of person email belongs to | | email | string | true | none | Email to be used. | | content | string | true | none | The base64-encoded contents of the file. | | type | string | true | none | The type of file being attached. | | filename | string | true | none | The name of the file being attached. | | disposition | string | true | none | Inline for content that can be displayed within the email, or attachment for any other files. | | content_id | string | true | none | An ID for the content. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$calculate_email_price_request = new \ClickSend\Model\CalculateEmailPriceRequest(); // \ClickSend\Model\CalculateEmailPriceRequest

try {
    $result = $apiInstance->calculateEmailPrice($content_type, $calculate_email_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->calculateEmailPrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **calculate_email_price_request** | [**\ClickSend\Model\CalculateEmailPriceRequest**](../Model/CalculateEmailPriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateEmailPrice**](../Model/CalculateEmailPrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelEmailCampaign()`

```php
cancelEmailCampaign($email_campaign_id, $content_type, $cancel_email_campaign_request): \ClickSend\Model\CancelEmailCampaign
```

Cancel Email Campaign

_Cancel email campaign_  Cancel email campaign  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_campaign_id | path | integer(int32) | true | Allowed email campaign id | | date_from | query | integer(int32) | false | Start date (Unix Timestamp e.g. 1436849372) | | date_to | query | integer(int32) | false | End date (Unix Timestamp e.g. 1436879372) | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_campaign_id = 'email_campaign_id_example'; // string
$content_type = application/json; // string
$cancel_email_campaign_request = new \ClickSend\Model\CancelEmailCampaignRequest(); // \ClickSend\Model\CancelEmailCampaignRequest

try {
    $result = $apiInstance->cancelEmailCampaign($email_campaign_id, $content_type, $cancel_email_campaign_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->cancelEmailCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **cancel_email_campaign_request** | [**\ClickSend\Model\CancelEmailCampaignRequest**](../Model/CancelEmailCampaignRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CancelEmailCampaign**](../Model/CancelEmailCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createAllowedEmailAddress()`

```php
createAllowedEmailAddress($content_type, $create_allowed_email_address_request): \ClickSend\Model\CreateAllowedEmailAddress
```

Create Allowed Email Address

_Create allowed Email Address_  Create allowed Email Address  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | body | body | string | true | Email to be allowed. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_allowed_email_address_request = new \ClickSend\Model\CreateAllowedEmailAddressRequest(); // \ClickSend\Model\CreateAllowedEmailAddressRequest

try {
    $result = $apiInstance->createAllowedEmailAddress($content_type, $create_allowed_email_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->createAllowedEmailAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_allowed_email_address_request** | [**\ClickSend\Model\CreateAllowedEmailAddressRequest**](../Model/CreateAllowedEmailAddressRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateAllowedEmailAddress**](../Model/CreateAllowedEmailAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createEmailDeliveryReceiptRule()`

```php
createEmailDeliveryReceiptRule($content_type, $create_sms_delivery_receipt_rule_request): \ClickSend\Model\CreateEmailDeliveryReceiptRule
```

Create Email Delivery Receipt Rule

_Create email delivery receipt automations_  Create email delivery receipt automations  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_sms_delivery_receipt_rule_request = new \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->createEmailDeliveryReceiptRule($content_type, $create_sms_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->createEmailDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_sms_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest**](../Model/CreateSmsDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateEmailDeliveryReceiptRule**](../Model/CreateEmailDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createEmailTemplate()`

```php
createEmailTemplate($content_type, $create_email_template_request): \ClickSend\Model\CreateEmailTemplate
```

Create Email Template

_Create email template_  Create email template  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | template_name | string | true | none | The intended name for the new template. | | template_id_master | number | true | none | The ID of the master template you want to base on. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_email_template_request = new \ClickSend\Model\CreateEmailTemplateRequest(); // \ClickSend\Model\CreateEmailTemplateRequest

try {
    $result = $apiInstance->createEmailTemplate($content_type, $create_email_template_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->createEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_email_template_request** | [**\ClickSend\Model\CreateEmailTemplateRequest**](../Model/CreateEmailTemplateRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateEmailTemplate**](../Model/CreateEmailTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteAllowedEmailAddress()`

```php
deleteAllowedEmailAddress($email_address_id, $content_type): \ClickSend\Model\DeleteAllowedEmailAddress
```

Delete Allowed Email Address

_Delete specific email address_  Delete specific email address  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_address_id | path | integer(int32) | true | Allowed email address id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_address_id = 'email_address_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteAllowedEmailAddress($email_address_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->deleteAllowedEmailAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_address_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteAllowedEmailAddress**](../Model/DeleteAllowedEmailAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteEmailDeliveryReceiptRule()`

```php
deleteEmailDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\DeleteEmailDeliveryReceiptRule
```

Delete Email Delivery Receipt Rule

_Delete email delivery receipt automation_  Delete email delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteEmailDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->deleteEmailDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteEmailDeliveryReceiptRule**](../Model/DeleteEmailDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteEmailTemplate()`

```php
deleteEmailTemplate($template_id, $content_type): \ClickSend\Model\DeleteEmailTemplate
```

Delete Email Template

_Delete user email template_  Delete user email template  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | template_id | path | integer(int32) | true | Email template id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->deleteEmailTemplate($template_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->deleteEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\DeleteEmailTemplate**](../Model/DeleteEmailTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportEmailCampaignHistory()`

```php
exportEmailCampaignHistory($email_campaign_id, $content_type)
```

Export Email Campaign History

_Export specific email campaign history_  Export specific email campaign history  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_campaign_id | path | integer(int32) | true | Allowed email campaign id | | date_from | query | integer(int32) | false | Start date (Unix Timestamp e.g. 1436849372) | | date_to | query | integer(int32) | false | End date (Unix Timestamp e.g. 1436879372) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_campaign_id = 'email_campaign_id_example'; // string
$content_type = application/json; // string

try {
    $apiInstance->exportEmailCampaignHistory($email_campaign_id, $content_type);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->exportEmailCampaignHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

void (empty response body)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportEmailHistory()`

```php
exportEmailHistory($content_type): \ClickSend\Model\ExportEmailHistory
```

Export Email History

_Export all Transactional Email history_  Export all Transactional Email history  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | filename | query | string | true | Filename to download history as | | date_from | query | integer(int32) | false | Start date (Unix Timestamp e.g. 1436849372) | | date_to | query | integer(int32) | false | End date (Unix Timestamp e.g. 1436879372) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->exportEmailHistory($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->exportEmailHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ExportEmailHistory**](../Model/ExportEmailHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendEmail()`

```php
sendEmail($content_type, $send_email_request): \ClickSend\Model\SendEmail
```

Send Email

_Send transactional email_  Send transactional email  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | to | array | true | none | Array of To Recipient items. (array of names and emails) | | cc | array | false | none | Array of Cc Recipient items. (array of names and emails) | | bcc | array | false | none | Array of Bcc Recipient items. (array of names and emails) | | from | object | true | none | From Email object. (object containing name and email) | | body | string | true | none | Body of the email. | | attachments | array | false | none | Array of Attachment items. | | schedule | number | false | none | Schedule. | | name | string | false | none | Name of person email belongs to | | email | string | true | none | Email to be used. | | content | string | true | none | The base64-encoded contents of the file. | | type | string | true | none | The type of file being attached. | | filename | string | true | none | The name of the file being attached. | | disposition | string | true | none | Inline for content that can be displayed within the email, or attachment for any other files. | | content_id | string | true | none | An ID for the content. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_email_request = new \ClickSend\Model\SendEmailRequest(); // \ClickSend\Model\SendEmailRequest

try {
    $result = $apiInstance->sendEmail($content_type, $send_email_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->sendEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_email_request** | [**\ClickSend\Model\SendEmailRequest**](../Model/SendEmailRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendEmail**](../Model/SendEmail.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendEmailCampaign()`

```php
sendEmailCampaign($content_type, $send_email_campaign_request): \ClickSend\Model\SendEmailCampaign
```

Send Email Campaign

_Send email campaign_  Send email campaign  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | name | string | true | none | Your campaign name. | | subject | string | true | none | Your campaign subject. | | body | string | true | none | Your campaign message. | | from_email_address_id | number | true | none | The allowed email address id. | | from_name | string | true | none | Your name or business name. | | template_id | number | false | none | Your template id. | | list_id | number | true | none | Your contact list id. | | schedule | integer(int32) | false | none | Your schedule timestamp. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_email_campaign_request = new \ClickSend\Model\SendEmailCampaignRequest(); // \ClickSend\Model\SendEmailCampaignRequest

try {
    $result = $apiInstance->sendEmailCampaign($content_type, $send_email_campaign_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->sendEmailCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_email_campaign_request** | [**\ClickSend\Model\SendEmailCampaignRequest**](../Model/SendEmailCampaignRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendEmailCampaign**](../Model/SendEmailCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendEmailVerificationToken()`

```php
sendEmailVerificationToken($email_address_id, $content_type, $send_email_verification_token_request): \ClickSend\Model\SendEmailVerificationToken
```

Send Email Verification Token

_Send verification token_  Send verification token  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_address_id | path | integer(int32) | true | Allowed email address id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_address_id = 'email_address_id_example'; // string
$content_type = application/json; // string
$send_email_verification_token_request = new \ClickSend\Model\SendEmailVerificationTokenRequest(); // \ClickSend\Model\SendEmailVerificationTokenRequest

try {
    $result = $apiInstance->sendEmailVerificationToken($email_address_id, $content_type, $send_email_verification_token_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->sendEmailVerificationToken: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_address_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **send_email_verification_token_request** | [**\ClickSend\Model\SendEmailVerificationTokenRequest**](../Model/SendEmailVerificationTokenRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendEmailVerificationToken**](../Model/SendEmailVerificationToken.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateEmailCampaign()`

```php
updateEmailCampaign($email_campaign_id, $content_type, $update_email_campaign_request): \ClickSend\Model\UpdateEmailCampaign
```

Update Email Campaign

_Edit email campaign_  Edit email campaign  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_campaign_id | path | integer(int32) | true | Allowed email campaign id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_campaign_id = 'email_campaign_id_example'; // string
$content_type = application/json; // string
$update_email_campaign_request = new \ClickSend\Model\UpdateEmailCampaignRequest(); // \ClickSend\Model\UpdateEmailCampaignRequest

try {
    $result = $apiInstance->updateEmailCampaign($email_campaign_id, $content_type, $update_email_campaign_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->updateEmailCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_email_campaign_request** | [**\ClickSend\Model\UpdateEmailCampaignRequest**](../Model/UpdateEmailCampaignRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateEmailCampaign**](../Model/UpdateEmailCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateEmailDeliveryReceiptRule()`

```php
updateEmailDeliveryReceiptRule($receipt_rule_id, $content_type, $create_sms_delivery_receipt_rule_request): \ClickSend\Model\UpdateEmailDeliveryReceiptRule
```

Update Email Delivery Receipt Rule

_Update email delivery receipt automation_  Update email delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | rule_name | string | true | none | Rule Name. | | match_type | number | true | none | Match Type. 0=All reports. | | action | string | true | none | Action to be taken (AUTO_REPLY, EMAIL_USER, EMAIL_FIXED, URL, SMS, POLL, GROUP_SMS, MOVE_CONTACT, CREATE_CONTACT, CREATE_CONTACT_PLUS_EMAIL, CREATE_CONTACT_PLUS_NAME_EMAIL CREATE_CONTACT_PLUS_NAME, SMPP, NONE). | | action_address | string | true | none | Action address. | | enabled | number | true | none | Enabled: Disabled=0 or Enabled=1. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string
$create_sms_delivery_receipt_rule_request = new \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest(); // \ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest

try {
    $result = $apiInstance->updateEmailDeliveryReceiptRule($receipt_rule_id, $content_type, $create_sms_delivery_receipt_rule_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->updateEmailDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **create_sms_delivery_receipt_rule_request** | [**\ClickSend\Model\CreateSmsDeliveryReceiptRuleRequest**](../Model/CreateSmsDeliveryReceiptRuleRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateEmailDeliveryReceiptRule**](../Model/UpdateEmailDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateEmailTemplate()`

```php
updateEmailTemplate($template_id, $content_type, $update_email_template_request): \ClickSend\Model\UpdateEmailTemplate
```

Update Email Template

_Update email template_  Update email template  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | template_id | path | integer(int32) | true | Email template id |  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | template_name | string | false | none | The intended name for the template. | | body | string | true | none | Your template body. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string
$content_type = application/json; // string
$update_email_template_request = new \ClickSend\Model\UpdateEmailTemplateRequest(); // \ClickSend\Model\UpdateEmailTemplateRequest

try {
    $result = $apiInstance->updateEmailTemplate($template_id, $content_type, $update_email_template_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->updateEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **update_email_template_request** | [**\ClickSend\Model\UpdateEmailTemplateRequest**](../Model/UpdateEmailTemplateRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateEmailTemplate**](../Model/UpdateEmailTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyAllowedEmailAddress()`

```php
verifyAllowedEmailAddress($email_address_id, $activation_token, $content_type, $verify_allowed_email_address_request): \ClickSend\Model\VerifyAllowedEmailAddress
```

Verify Allowed Email Address

_Verify email address using verification token_  Verify email address using verification token  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_address_id | path | integer(int32) | true | Allowed email address id | | activation_token | path | string | true | Your activation token. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_address_id = 'email_address_id_example'; // string
$activation_token = 'activation_token_example'; // string
$content_type = application/json; // string
$verify_allowed_email_address_request = new \ClickSend\Model\VerifyAllowedEmailAddressRequest(); // \ClickSend\Model\VerifyAllowedEmailAddressRequest

try {
    $result = $apiInstance->verifyAllowedEmailAddress($email_address_id, $activation_token, $content_type, $verify_allowed_email_address_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->verifyAllowedEmailAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_address_id** | **string**|  | |
| **activation_token** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **verify_allowed_email_address_request** | [**\ClickSend\Model\VerifyAllowedEmailAddressRequest**](../Model/VerifyAllowedEmailAddressRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\VerifyAllowedEmailAddress**](../Model/VerifyAllowedEmailAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAllEmailCampaigns()`

```php
viewAllEmailCampaigns($content_type): \ClickSend\Model\ViewAllEmailCampaigns
```

View All Email Campaigns

_Get all email campaigns_  Get all email campaigns  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAllEmailCampaigns($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewAllEmailCampaigns: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAllEmailCampaigns**](../Model/ViewAllEmailCampaigns.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAllowedEmailAddress()`

```php
viewAllowedEmailAddress($email_address_id, $content_type): \ClickSend\Model\ViewAllowedEmailAddress
```

View Allowed Email Address

_Get specific email address_  Get specific email address  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | email_address_id | path | integer(int32) | true | Allowed email address id |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_address_id = 'email_address_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAllowedEmailAddress($email_address_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewAllowedEmailAddress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_address_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAllowedEmailAddress**](../Model/ViewAllowedEmailAddress.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewAllowedEmailAddresses()`

```php
viewAllowedEmailAddresses($content_type): \ClickSend\Model\ViewAllowedEmailAddresses
```

View Allowed Email Addresses

_Get all email addresses_  Get all email addresses  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewAllowedEmailAddresses($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewAllowedEmailAddresses: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewAllowedEmailAddresses**](../Model/ViewAllowedEmailAddresses.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailCampaign()`

```php
viewEmailCampaign($email_campaign_id, $content_type): \ClickSend\Model\ViewEmailCampaign
```

View Email Campaign

_Get specific email campaign_  Get specific email campaign  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_campaign_id = 'email_campaign_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailCampaign($email_campaign_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailCampaign: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailCampaign**](../Model/ViewEmailCampaign.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailCampaignHistory()`

```php
viewEmailCampaignHistory($email_campaign_id, $content_type): \ClickSend\Model\ViewEmailCampaignHistory
```

View Email Campaign History

_Get specific email campaign history_  Get specific email campaign history   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email_campaign_id = 'email_campaign_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailCampaignHistory($email_campaign_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailCampaignHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email_campaign_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailCampaignHistory**](../Model/ViewEmailCampaignHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailDeliveryReceiptRule()`

```php
viewEmailDeliveryReceiptRule($receipt_rule_id, $content_type): \ClickSend\Model\ViewEmailDeliveryReceiptRule
```

View Email Delivery Receipt Rule

_Get specific email delivery receipt automation_  Get specific email delivery receipt automation  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | receipt_rule_id | path | integer(int32) | true | Receipt rule id |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$receipt_rule_id = 'receipt_rule_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailDeliveryReceiptRule($receipt_rule_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailDeliveryReceiptRule: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **receipt_rule_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailDeliveryReceiptRule**](../Model/ViewEmailDeliveryReceiptRule.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailDeliveryReceiptRules()`

```php
viewEmailDeliveryReceiptRules($content_type): \ClickSend\Model\ViewEmailDeliveryReceiptRules
```

View Email Delivery Receipt Rules

_Get all email delivery receipt automations_  Get all email delivery receipt automations  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailDeliveryReceiptRules($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailDeliveryReceiptRules: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailDeliveryReceiptRules**](../Model/ViewEmailDeliveryReceiptRules.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailHistory()`

```php
viewEmailHistory($content_type): \ClickSend\Model\ViewEmailHistory
```

View Email History

_Get all transactional email history_  Get all transactional email history  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | date_from | query | integer(int32) | false | Start date (Unix Timestamp e.g. 1436849372) | | date_to | query | integer(int32) | false | End date (Unix Timestamp e.g. 1436879372) | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailHistory($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailHistory**](../Model/ViewEmailHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailTemplate()`

```php
viewEmailTemplate($template_id, $content_type): \ClickSend\Model\ViewEmailTemplate
```

View Email Template

_Get specific user email template_  Get specific user email templates  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | template_id | path | integer(int32) | true | Email template id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailTemplate($template_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailTemplate**](../Model/ViewEmailTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewEmailTemplates()`

```php
viewEmailTemplates($content_type): \ClickSend\Model\ViewEmailTemplates
```

View Email Templates

_Get all user email templates_  Get all user email templates  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewEmailTemplates($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewEmailTemplates: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewEmailTemplates**](../Model/ViewEmailTemplates.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewMasterEmailTemplate()`

```php
viewMasterEmailTemplate($template_id, $content_type): \ClickSend\Model\ViewMasterEmailTemplate
```

View Master Email Template

_Get specific master email template_  Get specific master email template  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | template_id | path | integer(int32) | true | Email template id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_id = 'template_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewMasterEmailTemplate($template_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewMasterEmailTemplate: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewMasterEmailTemplate**](../Model/ViewMasterEmailTemplate.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewMasterEmailTemplates()`

```php
viewMasterEmailTemplates($content_type): \ClickSend\Model\ViewMasterEmailTemplates
```

View Master Email Templates

_Get all master email templates._  Get all master email templates.  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewMasterEmailTemplates($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewMasterEmailTemplates: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewMasterEmailTemplates**](../Model/ViewMasterEmailTemplates.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewTemplateCategories()`

```php
viewTemplateCategories($content_type): \ClickSend\Model\ViewTemplateCategories
```

View Template Categories

_Get all master email template categories_  Get all master email template categories  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewTemplateCategories($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewTemplateCategories: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewTemplateCategories**](../Model/ViewTemplateCategories.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewTemplateCategory()`

```php
viewTemplateCategory($category_id, $content_type): \ClickSend\Model\ViewTemplateCategory
```

View Template Category

_Get specific master email template category_  Get specific master email template category  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | category_id | path | integer(int32) | true | Email category id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$category_id = 'category_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewTemplateCategory($category_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewTemplateCategory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **category_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewTemplateCategory**](../Model/ViewTemplateCategory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewTemplatesInCategory()`

```php
viewTemplatesInCategory($category_id, $content_type): \ClickSend\Model\ViewTemplatesInCategory
```

View Templates in Category

_Get all master email templates in a category_  Get all master email templates in a category  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | category_id | path | integer(int32) | true | Email category id | | page | query | integer(int32) | false | Page number | | limit | query | integer(int32) | false | Number of records per page |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\EmailApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$category_id = 'category_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->viewTemplatesInCategory($category_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EmailApi->viewTemplatesInCategory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **category_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewTemplatesInCategory**](../Model/ViewTemplatesInCategory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
