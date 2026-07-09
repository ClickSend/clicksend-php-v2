# ClickSend\DefaultSendersApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createDefaultSender()**](DefaultSendersApi.md#createDefaultSender) | **POST** /v3/senders/default-senders | Create Default Sender |
| [**deleteDefaultSender()**](DefaultSendersApi.md#deleteDefaultSender) | **DELETE** /v3/senders/default-senders/{default_sender_id} | Delete Default Sender |
| [**getDefaultSenderDetails()**](DefaultSendersApi.md#getDefaultSenderDetails) | **GET** /v3/senders/default-senders/{default_sender_id} | Get Default Sender Details |
| [**getDefaultSendersList()**](DefaultSendersApi.md#getDefaultSendersList) | **GET** /v3/senders/default-senders | Get List of Default Senders |
| [**listCompliantSenderTypes()**](DefaultSendersApi.md#listCompliantSenderTypes) | **GET** /v3/senders/compliant-sender-types | List Compliant Sender Types |
| [**updateDefaultSender()**](DefaultSendersApi.md#updateDefaultSender) | **PATCH** /v3/senders/default-senders/{default_sender_id} | Update Default Sender |


## `createDefaultSender()`

```php
createDefaultSender($content_type, $create_default_sender_request): \ClickSend\Model\CreateDefaultSender
```

Create Default Sender

Creates a new default sender configuration to automate the selection of compliant SenderIDs. By configuring a default sender you no longer need to define the `sender_id` string when sending SMS messages. The default sender will be picked up automatically.  For more information on Sender IDs, please refer to [What is a Sender ID or Sender Number?](https://help.clicksend.com/article/4kgj7krx00-what-is-a-sender-id-or-sender-number)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\DefaultSendersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$create_default_sender_request = new \ClickSend\Model\CreateDefaultSenderRequest(); // \ClickSend\Model\CreateDefaultSenderRequest

try {
    $result = $apiInstance->createDefaultSender($content_type, $create_default_sender_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DefaultSendersApi->createDefaultSender: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **create_default_sender_request** | [**\ClickSend\Model\CreateDefaultSenderRequest**](../Model/CreateDefaultSenderRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CreateDefaultSender**](../Model/CreateDefaultSender.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteDefaultSender()`

```php
deleteDefaultSender($default_sender_id, $content_type)
```

Delete Default Sender

Removes a specified default sender setting.  If you don't configure a default sender and leave the `sender_id` string blank when sending an SMS, Smart Assign will pick the best suitable, compliant, available SenderID for you.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\DefaultSendersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$default_sender_id = 'default_sender_id_example'; // string | The ID of the default sender to delete
$content_type = application/json; // string

try {
    $apiInstance->deleteDefaultSender($default_sender_id, $content_type);
} catch (Exception $e) {
    echo 'Exception when calling DefaultSendersApi->deleteDefaultSender: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **default_sender_id** | **string**| The ID of the default sender to delete | |
| **content_type** | **string**|  | [optional] |

### Return type

void (empty response body)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDefaultSenderDetails()`

```php
getDefaultSenderDetails($default_sender_id, $content_type): \ClickSend\Model\GetDefaultSenderDetails
```

Get Default Sender Details

Retrieve detailed information about a specific default sender configuration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\DefaultSendersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$default_sender_id = 'default_sender_id_example'; // string | The ID of the default sender to retrieve
$content_type = application/json; // string

try {
    $result = $apiInstance->getDefaultSenderDetails($default_sender_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DefaultSendersApi->getDefaultSenderDetails: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **default_sender_id** | **string**| The ID of the default sender to retrieve | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\GetDefaultSenderDetails**](../Model/GetDefaultSenderDetails.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDefaultSendersList()`

```php
getDefaultSendersList($content_type, $offset, $per_page, $sort_by, $sort_direction): \ClickSend\Model\GetDefaultSendersList
```

Get List of Default Senders

Retrieve a list of default senders for the current user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\DefaultSendersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$offset = 'offset_example'; // string | Page (offset) to be used for pagination
$per_page = 10; // int | Size of the page in pagination
$sort_by = 'created_timestamp'; // string | Parameter to sort the results by
$sort_direction = 'desc'; // string | Direction of sorting

try {
    $result = $apiInstance->getDefaultSendersList($content_type, $offset, $per_page, $sort_by, $sort_direction);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DefaultSendersApi->getDefaultSendersList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **offset** | **string**| Page (offset) to be used for pagination | [optional] |
| **per_page** | **int**| Size of the page in pagination | [optional] [default to 10] |
| **sort_by** | **string**| Parameter to sort the results by | [optional] [default to &#39;created_timestamp&#39;] |
| **sort_direction** | **string**| Direction of sorting | [optional] [default to &#39;desc&#39;] |

### Return type

[**\ClickSend\Model\GetDefaultSendersList**](../Model/GetDefaultSendersList.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCompliantSenderTypes()`

```php
listCompliantSenderTypes($filter_product_type, $filter_country_code_index): \ClickSend\Model\ListCompliantSenderTypes200Response
```

List Compliant Sender Types

Retrieves the list of compliant sender types for specific countries

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\DefaultSendersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$filter_product_type = SMS; // string | Type of the product
$filter_country_code_index = array('filter_country_code_index_example'); // string[] | Array of recipient country codes (ISO 3166-1 alpha-2). If not specified, will get all compliant sender types for all countries. Replace `{index}` with the appropriate index value.  <small>Example:</small> <small><code style=\"color: #424242;\">filter[country_code][0]=US&filter[country_code][1]=AU</code></small>

try {
    $result = $apiInstance->listCompliantSenderTypes($filter_product_type, $filter_country_code_index);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DefaultSendersApi->listCompliantSenderTypes: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **filter_product_type** | **string**| Type of the product | |
| **filter_country_code_index** | [**string[]**](../Model/string.md)| Array of recipient country codes (ISO 3166-1 alpha-2). If not specified, will get all compliant sender types for all countries. Replace &#x60;{index}&#x60; with the appropriate index value.  &lt;small&gt;Example:&lt;/small&gt; &lt;small&gt;&lt;code style&#x3D;\&quot;color: #424242;\&quot;&gt;filter[country_code][0]&#x3D;US&amp;filter[country_code][1]&#x3D;AU&lt;/code&gt;&lt;/small&gt; | [optional] |

### Return type

[**\ClickSend\Model\ListCompliantSenderTypes200Response**](../Model/ListCompliantSenderTypes200Response.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateDefaultSender()`

```php
updateDefaultSender($default_sender_id, $content_type, $update_default_sender_request): \ClickSend\Model\UpdateDefaultSender
```

Update Default Sender

Updates the details of an existing default sender configuration.  For more information on Sender IDs, please refer to [What is a Sender ID or Sender Number?](https://help.clicksend.com/article/4kgj7krx00-what-is-a-sender-id-or-sender-number)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\DefaultSendersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$default_sender_id = 'default_sender_id_example'; // string | The ID of the default sender to update
$content_type = application/json; // string
$update_default_sender_request = new \ClickSend\Model\UpdateDefaultSenderRequest(); // \ClickSend\Model\UpdateDefaultSenderRequest

try {
    $result = $apiInstance->updateDefaultSender($default_sender_id, $content_type, $update_default_sender_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DefaultSendersApi->updateDefaultSender: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **default_sender_id** | **string**| The ID of the default sender to update | |
| **content_type** | **string**|  | [optional] |
| **update_default_sender_request** | [**\ClickSend\Model\UpdateDefaultSenderRequest**](../Model/UpdateDefaultSenderRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\UpdateDefaultSender**](../Model/UpdateDefaultSender.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
