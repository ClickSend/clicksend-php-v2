# ClickSend\VerificationApi



All URIs are relative to https://rest.clicksend.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**forgotPassword()**](VerificationApi.md#forgotPassword) | **PUT** /v3/forgot-password | Forgot Password |
| [**forgotUsername()**](VerificationApi.md#forgotUsername) | **PUT** /v3/forgot-username | Forgot Username |


## `forgotPassword()`

```php
forgotPassword($content_type, $forgot_password_request): \ClickSend\Model\ForgotPassword
```

Forgot Password

_Forgot password_  A user can send their username to this endpoint to be sent an email with their registered email address that will have a verification code.  Once you have this verification email containing the code you can send it to the [forgotten-password/verify](/#verify-forgot-password) endpoint along with a new password and the ID of that subaccount.  _Ask your administrator if you do not know your subaccount id._  ### Properties  | **Name** | **Type** | **Required** | **Restrictions** | **Description** | | --- | --- | --- | --- | --- | | username | string | true | none | Username belonging to account |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #6BBD5B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint does not require authentication</span>  </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VerificationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$forgot_password_request = new \ClickSend\Model\ForgotPasswordRequest(); // \ClickSend\Model\ForgotPasswordRequest

try {
    $result = $apiInstance->forgotPassword($content_type, $forgot_password_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VerificationApi->forgotPassword: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **forgot_password_request** | [**\ClickSend\Model\ForgotPasswordRequest**](../Model/ForgotPasswordRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\ForgotPassword**](../Model/ForgotPassword.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `forgotUsername()`

```php
forgotUsername($content_type, $forgot_username_request): \ClickSend\Model\ForgotUsername
```

Forgot Username

_Forgot username_  Requires the user to pass either the email registered to an account or the phone number, **not** both  ### Properties  | **Name** | **Type** | **Required** | **Restrictions** | **Description** | | --- | --- | --- | --- | --- | | email | string | true | none | Email belonging to account | | phone_number | string | true | none | Phone belonging to account |  Refer to [Status Codes](/#status-codes) for definitions of HTTP status code responses.  <div style=\"background-color: #6BBD5B; padding: 10px; border-radius: 8px;\">   <span style=\"color: white;\">This endpoint does not require authentication</span>  </div>

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure HTTP basic authorization: basicAuth
$config = ClickSend\Configuration::getDefaultConfiguration()
              ->setUsername('YOUR_USERNAME')
              ->setPassword('YOUR_PASSWORD');


$apiInstance = new ClickSend\Api\VerificationApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$content_type = application/json; // string
$forgot_username_request = new \ClickSend\Model\ForgotUsernameRequest(); // \ClickSend\Model\ForgotUsernameRequest

try {
    $result = $apiInstance->forgotUsername($content_type, $forgot_username_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling VerificationApi->forgotUsername: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **content_type** | **string**|  | [optional] |
| **forgot_username_request** | [**\ClickSend\Model\ForgotUsernameRequest**](../Model/ForgotUsernameRequest.md)|  | [optional] |

### Return type

[**\ClickSend\Model\ForgotUsername**](../Model/ForgotUsername.md)

### Authorization

[basicAuth](../../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
