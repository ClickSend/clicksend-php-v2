# ClickSend\AlphaTagsApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**deleteAlphaTag()**](AlphaTagsApi.md#deleteAlphaTag) | **DELETE** /v3/alpha-tags/{alpha_tag_id} | Delete Alpha Tag |
| [**getAlphaTag()**](AlphaTagsApi.md#getAlphaTag) | **GET** /v3/alpha-tags/{alpha_tag_id} | Get Alpha Tag |
| [**listAlphaTags()**](AlphaTagsApi.md#listAlphaTags) | **GET** /v3/alpha-tags | List Alpha Tags |
| [**requestAlphaTag()**](AlphaTagsApi.md#requestAlphaTag) | **POST** /v3/alpha-tags | Request Alpha Tag |


## `deleteAlphaTag()`

```php
deleteAlphaTag($alpha_tag_id, $content_type)
```

Delete Alpha Tag

_Delete a specific alpha tag._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | alpha_tag_id | path | uuid | true | ID of the alpha tag |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AlphaTagsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$alpha_tag_id = 'alpha_tag_id_example'; // string
$content_type = application/json; // string

try {
    $apiInstance->deleteAlphaTag($alpha_tag_id, $content_type);
} catch (Exception $e) {
    echo 'Exception when calling AlphaTagsApi->deleteAlphaTag: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **alpha_tag_id** | **string**|  | |
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

## `getAlphaTag()`

```php
getAlphaTag($alpha_tag_id, $content_type): \ClickSend\Model\AlphaTag
```

Get Alpha Tag

_Get a specific alpha tag._  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | alpha_tag_id | path | uuid | true | ID of the alpha tag |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   This endpoint requires authentication, [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AlphaTagsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$alpha_tag_id = 'alpha_tag_id_example'; // string
$content_type = application/json; // string

try {
    $result = $apiInstance->getAlphaTag($alpha_tag_id, $content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AlphaTagsApi->getAlphaTag: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **alpha_tag_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\AlphaTag**](../Model/AlphaTag.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listAlphaTags()`

```php
listAlphaTags($sort_direction, $page_size): \ClickSend\Model\ListAlphaTags
```

List Alpha Tags



### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AlphaTagsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$sort_direction = asc; // string | The sort direction for the results. The default value is asc.
$page_size = 10; // int | The number of items to return per page. This parameter controls the size of each page of results. The default value is 10.

try {
    $result = $apiInstance->listAlphaTags($sort_direction, $page_size);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AlphaTagsApi->listAlphaTags: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **sort_direction** | **string**| The sort direction for the results. The default value is asc. | [optional] [default to &#39;asc&#39;] |
| **page_size** | **int**| The number of items to return per page. This parameter controls the size of each page of results. The default value is 10. | [optional] [default to 10] |

### Return type

[**\ClickSend\Model\ListAlphaTags**](../Model/ListAlphaTags.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `requestAlphaTag()`

```php
requestAlphaTag($content_type, $request_alpha_tag_request): \ClickSend\Model\AlphaTag
```

Request Alpha Tag

_Request to register an alpha tag. After requested, the alpha tag will be reviewed by ClickSend and either approved or rejected. Some countries (e.g Australia) require you to submit additional fields due to government mandated compliance checks._  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | alpha_tag | string | true | [yes](https://help.clicksend.com/article/1qxfxkcwm2-global-generic-alpha-tags) | The alpha tag name. Length must be between 3 - 11 characters, can only contain a-z A-Z 0-9 + and must contain at least one non numeric. | | reason | string | false | none | Must be one of the following: `Sole Trader Name`, `Company Name`, `Partnership Name`, `Registered Trust Name`, `Co-Operative Name`, `Indigenous Corporation Name`, `Registered Organisation Name`, `Personal Name`, `Trademark`, `Government Agency or Entity`, `Product or Service Name`, `Acronym/Initialism`, `Contraction of Name`, `Third Party`. In case of `Third Party`, we will contact you to collect the relevant information. | | countries | array of strings | false | none | List of country codes (e.g., \"AU\", \"US\") where the alpha tag is requested. Only supported and required for AU. | | businesses | array of objects | false | none | List of business details required for alpha tag registration. Each object contains country, business information, ... Required if `countries` is provided. When `business_relationship` is `ENTITY_ASSOCIATE`, the following partner fields are also **required**: `partner_business_name`, `partner_abn`, `partner_business_info`, `partner_business_address`, `partner_representative`. These fields are **forbidden** for any other `business_relationship` value. |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  _This endpoint requires authentication,_ [more info...](/#authentication)

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\AlphaTagsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$request_alpha_tag_request = {"alpha_tag":"MyCompany","reason":"Company Name"}; // \ClickSend\Model\RequestAlphaTagRequest

try {
    $result = $apiInstance->requestAlphaTag($content_type, $request_alpha_tag_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AlphaTagsApi->requestAlphaTag: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **request_alpha_tag_request** | [**\ClickSend\Model\RequestAlphaTagRequest**](../Model/RequestAlphaTagRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\AlphaTag**](../Model/AlphaTag.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
