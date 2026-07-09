# ClickSend\VoiceMessagingApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**calculateVoicePrice()**](VoiceMessagingApi.md#calculateVoicePrice) | **POST** /v3/voice/price | Calculate Voice Price |
| [**cancelAllVoiceMessages()**](VoiceMessagingApi.md#cancelAllVoiceMessages) | **PUT** /v3/voice/cancel-all | Cancel All Voice Messages |
| [**cancelVoiceMessage()**](VoiceMessagingApi.md#cancelVoiceMessage) | **PUT** /v3/voice/{message_id}/cancel | Cancel Voice Message |
| [**exportVoiceHistory()**](VoiceMessagingApi.md#exportVoiceHistory) | **GET** /v3/voice/history/export | Export Voice History |
| [**getVoiceHistory()**](VoiceMessagingApi.md#getVoiceHistory) | **GET** /v3/voice/history | Get Voice History |
| [**sendVoiceMessage()**](VoiceMessagingApi.md#sendVoiceMessage) | **POST** /v3/voice/send | Send Voice Message |
| [**viewVoiceLanguages()**](VoiceMessagingApi.md#viewVoiceLanguages) | **GET** /v3/voice/lang | View Voice Languages |
| [**viewVoiceReceipts()**](VoiceMessagingApi.md#viewVoiceReceipts) | **GET** /v3/voice/receipts | View Voice Receipts |


## `calculateVoicePrice()`

```php
calculateVoicePrice($content_type, $calculate_voice_price_request): \ClickSend\Model\CalculateVoicePrice
```

Calculate Voice Price

_Calculate voice price_  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | to | string | true | none | Your phone number in [E.164](https://en.wikipedia.org/wiki/E.164) format. | | body | string | true | none | Biscuit uv3nlCOjRk croissant chocolate lollipop chocolate muffin. | | voice | string | true | none | Either 'female' or 'male'. | | custom_string | string | true | none | Your reference. Will be passed back with all replies and delivery reports. | | country | string | true | none | The country of the recipient. | | source | string | false | none | Your method of sending e.g. 'wordpress', 'php', 'c#'. | | list_id | integer(int32) | false | none | Your list ID if sending to a whole list. Can be used instead of 'to'. | | lang | string | false | none | au (string, required) - See section on available languages. | | schedule | integer(int32) | false | none | Leave blank for immediate delivery. Your schedule time in unix format [http://help.clicksend.com/what-is-a-unix-timestamp](http://help.clicksend.com/what-is-a-unix-timestamp) | | require_input | integer(int1) | false | none | Recieve a keypress from the recipient. Flag value must be 1 for yes or 0 for no. | | machine_detection | integer(int1) | false | none | Detect answering machine or voicemail and leave a message. Flag value must be 1 for yes or 0 for no. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$calculate_voice_price_request = new \ClickSend\Model\CalculateVoicePriceRequest(); // \ClickSend\Model\CalculateVoicePriceRequest

try {
    $result = $apiInstance->calculateVoicePrice($content_type, $calculate_voice_price_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->calculateVoicePrice: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **calculate_voice_price_request** | [**\ClickSend\Model\CalculateVoicePriceRequest**](../Model/CalculateVoicePriceRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\CalculateVoicePrice**](../Model/CalculateVoicePrice.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelAllVoiceMessages()`

```php
cancelAllVoiceMessages($content_type, $body): \ClickSend\Model\CancelAllVoiceMessages
```

Cancel All Voice Messages

_Update all voice messages as cancelled_  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/x-www-form-urlencoded; // string
$body = array('key' => new \stdClass); // object

try {
    $result = $apiInstance->cancelAllVoiceMessages($content_type, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->cancelAllVoiceMessages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **body** | **object**|  | [optional] |

### Return type

[**\ClickSend\Model\CancelAllVoiceMessages**](../Model/CancelAllVoiceMessages.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelVoiceMessage()`

```php
cancelVoiceMessage($message_id, $content_type, $body): \ClickSend\Model\CancelVoiceMessage
```

Cancel Voice Message

_Update voice message status as cancelled_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | message_id | path | string | true | Your voice message id |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$message_id = 'message_id_example'; // string
$content_type = application/x-www-form-urlencoded; // string
$body = array('key' => new \stdClass); // object

try {
    $result = $apiInstance->cancelVoiceMessage($message_id, $content_type, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->cancelVoiceMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **message_id** | **string**|  | |
| **content_type** | **string**|  | [optional] |
| **body** | **object**|  | [optional] |

### Return type

[**\ClickSend\Model\CancelVoiceMessage**](../Model/CancelVoiceMessage.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportVoiceHistory()`

```php
exportVoiceHistory($content_type, $filename, $q, $order_by, $date_from, $date_to, $limit): \ClickSend\Model\ExportVoiceHistory
```

Export Voice History

_Export voice history_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | filename | query | string | true | Filename to export to |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$filename = Voice_history.csv; // string
$q = 'q_example'; // string
$order_by = date_added:desc; // string
$date_from = 'date_from_example'; // string
$date_to = 'date_to_example'; // string
$limit = 50000; // int

try {
    $result = $apiInstance->exportVoiceHistory($content_type, $filename, $q, $order_by, $date_from, $date_to, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->exportVoiceHistory: ', $e->getMessage(), PHP_EOL;
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

[**\ClickSend\Model\ExportVoiceHistory**](../Model/ExportVoiceHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getVoiceHistory()`

```php
getVoiceHistory($content_type, $date_to, $limit, $operator, $order_by, $page): \ClickSend\Model\GetVoiceHistory
```

Get Voice History

_Get all voice history_  ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | date_from | query | integer(int32) | false | Start date (Unix Timestamp e.g. 1436849372) | | date_to | query | integer(int32) | false | End date (Unix Timestamp e.g. 1436879372) | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$date_to = 'date_to_example'; // string
$limit = 20; // int
$operator = AND; // string
$order_by = date_added:desc; // string
$page = 1; // int

try {
    $result = $apiInstance->getVoiceHistory($content_type, $date_to, $limit, $operator, $order_by, $page);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->getVoiceHistory: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **date_to** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] |
| **operator** | **string**|  | [optional] |
| **order_by** | **string**|  | [optional] |
| **page** | **int**|  | [optional] |

### Return type

[**\ClickSend\Model\GetVoiceHistory**](../Model/GetVoiceHistory.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendVoiceMessage()`

```php
sendVoiceMessage($content_type, $send_voice_message_request): \ClickSend\Model\SendVoiceMessage
```

Send Voice Message

_Send voice message(s)_  Send TTS (Text-to-speech) voice calls  ### How many messages can I send?  You can post **up to 1000 messages** with each API call. You can send to a mix of contacts and contact lists, as long as the total number of recipients is up to 1000. The response contains a status and details for each recipient.  ### How many characters can I send in a message?  If a message is longer than 4 message parts, it will be truncated (see below). If a message contains any characters that aren't in the GSM 03.38 character set, the message type will be treated as unicode. (`https://en.wikipedia.org/wiki/GSM_03.38`)  ### _Standard English Characters:_  | Number of Characters | Message Credits | | --- | --- | | 1 - 300 | 1 | | 301 - 600 | 2 | | 601 - 900 | 3 | | 901 - 1200 | 4 |  ### _Non-GSM (Unicode) characters:_  | Number of Characters | Message Credits | | --- | --- | | 1 - 150 | 1 | | 151 - 300 | 2 | | 301 - 450 | 3 | | 451 - 600 | 4 |  ### _Allowed Languages_  | Language, Locale | lang | voice | | --- | --- | --- | | `English`, US | en-us | female (default) / male | | `English`, Australia | en-au | female (default) / male | | `English`, UK | en-gb | female (default) / male | | `English`, India | en-in | female | | `English`, Wales | en-gb-wls | female (default) / male | | `Celtic`, Wales | cy-gb-wls | female (default) / male | | `German`, Germany | de-de | female (default) / male | | `Spanish`, Spain | es-es | female (default) / male | | `Spanish`, US | es-us | female (default) / male | | `French`, Canada | fr-ca | female | | `French`, France | fr-fr | female (default) / male | | `Icelandic`, Iceland | is-is | female (default) / male | | `Italian`, Italy | it-it | female (default) / male | | `Danish`, Denmark | da-dk | female (default) / male | | `Dutch`, Netherlands | nl-nl | female (default) / male | | `Norwegian`, Norway | nb-no | female | | `Polish`, Poland | pl-pl | female (default) / male | | `Portuguese`, Portugal | pt-pt | male | | `Portuguese`, Brazil | pt-br | female (default) / male | | `Romanian`, Romania | ro-ro | female | | `Russian`, Russia | ru-ru | female (default) / male | | `Swedish`, Sweden | sv-se | female | | `Turkish`, Turkey | tr-tr | female |  _Tips_  To introduce a small delay between words or digits you can use a comma (,).  For example: `Please enter your activation code 9, 0, 9, 0, in the next 20 minutes.`  We support some SSML tags allowing custom breaks or pauses to be entered, and the readout rate to be altered.  [More info...](https://help.clicksend.com/en/articles/42982-customising-text-to-voice-output)  ### Properties  | Name | Type | Required | Restrictions | Description | | --- | --- | --- | --- | --- | | to | string | true | none | Your phone number in [E.164](https://en.wikipedia.org/wiki/E.164) format. | | body | string | true | none | Biscuit uv3nlCOjRk croissant chocolate lollipop chocolate muffin. | | voice | string | true | none | Either 'female' or 'male'. | | custom_string | string | true | none | Your reference. Will be passed back with all replies and delivery reports. | | country | string | true | none | The country of the recipient. | | source | string | false | none | Your method of sending e.g. 'wordpress', 'php', 'c#'. | | list_id | integer(int32) | false | none | Your list ID if sending to a whole list. Can be used instead of 'to'. | | lang | string | false | none | au (string, required) - See section on available languages. | | schedule | integer(int32) | false | none | Leave blank for immediate delivery. Your schedule time in unix format [http://help.clicksend.com/what-is-a-unix-timestamp](http://help.clicksend.com/what-is-a-unix-timestamp) | | require_input | integer(int1) | false | none | Recieve a keypress from the recipient. Flag value must be 1 for yes or 0 for no. | | machine_detection | integer(int1) | false | none | Detect answering machine or voicemail and leave a message. Flag value must be 1 for yes or 0 for no. |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$send_voice_message_request = new \ClickSend\Model\SendVoiceMessageRequest(); // \ClickSend\Model\SendVoiceMessageRequest

try {
    $result = $apiInstance->sendVoiceMessage($content_type, $send_voice_message_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->sendVoiceMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **send_voice_message_request** | [**\ClickSend\Model\SendVoiceMessageRequest**](../Model/SendVoiceMessageRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\SendVoiceMessage**](../Model/SendVoiceMessage.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewVoiceLanguages()`

```php
viewVoiceLanguages($content_type): \ClickSend\Model\ViewVoiceLanguages
```

View Voice Languages

_Get all voice languages_   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewVoiceLanguages($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->viewVoiceLanguages: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewVoiceLanguages**](../Model/ViewVoiceLanguages.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `viewVoiceReceipts()`

```php
viewVoiceReceipts($content_type): \ClickSend\Model\ViewVoiceReceipts
```

View Voice Receipts

_Get all voice receipts_  **Push Delivery Receipts**  If you prefer, we can push message replies to your server as they arrive with us.  1. Log into your account. 2. Click on your profile on the top right. 3. Then click on the Messaging Settings option. 4. Click on Voice then Delivery Report Rules. 5. Click the 'Add New Rule' button. 6. Select the 'URL' action. 7. Enter the URL and click 'Save'.       The following variables will be posted to the URL specified:  | Variable | Description | | --- | --- | | `timestamp_send` | Timestamp of the original send request in UNIX format. e.g 1439173980 | | `timestamp` | Timestamp of delivery report in UNIX format. e.g 1439173981 | | `message_id` | Message ID, returned when originally sending the message. | | `status` | Delivered or Undelivered | | `status_code` | Status code. Refer to 'Voice Delivery Status Codes' in docs. | | `status_text` | Status text. | | `error_code` | Error code. | | `error_text` | Error text. | | `custom_string` | A custom string used when sending the original message. | | `user_id` | The user ID of the user who sent the message. | | `subaccount_id` | The subaccount ID of the user who sent the message. | | `message_type` | 'voice' (constant). | | `digits` | Numbers the recipient pressed on their keypad during the call. A blank string will be used if they didn't provide any input. |  **Pull Delivery Receipts**  Receive delivery reports by polling. You can poll our server and retrieve delivery reports at a time that suits you.  1. Log into your account. 2. Click on your profile on the top right. 3. Then click on the Messaging Settings option. 4. Click on Voice then Delivery Report Rules. 5. Click the 'Add New Rule' button. 6. Select the 'Poll' action. 7. Then click 'Save'.       ### Parameters  | Parameter | In | Type | Required | Description | | --- | --- | --- | --- | --- | | page | query | integer(int32) | false | [Page number](/#pagination) | | limit | query | integer(int32) | false | [Number of records per page](/#pagination) |   Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.   <div style=\"background-color: #FF6A4B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint requires authentication,</span>    <a href=\"/docs/#authentication\" style=\"color: white; text-decoration: underline;\">more info...</a> </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VoiceMessagingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string

try {
    $result = $apiInstance->viewVoiceReceipts($content_type);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VoiceMessagingApi->viewVoiceReceipts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |

### Return type

[**\ClickSend\Model\ViewVoiceReceipts**](../Model/ViewVoiceReceipts.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
