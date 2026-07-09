# VoiceReceipt

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**timestamp_send** | **string** | Timestamp of the original send request in UNIX format. e.g 1439173980 | [optional]
**timestamp** | **string** | Timestamp of delivery report in UNIX format. e.g 1439173981 | [optional]
**message_id** | **string** | Message ID, returned when originally sending the message. | [optional]
**status_code** | **string** | Status code. Refer to &#39;Voice Delivery Status Codes&#39; in docs. | [optional]
**status_text** | **string** | Status text. | [optional]
**error_code** | **string** | Error code. | [optional]
**error_text** | **string** | Error text. | [optional]
**custom_string** | **string** | A custom string used when sending the original message. | [optional]
**message_type** | **string** | voice (constant). | [optional]
**digits** | **string** | Numbers the recipient pressed on their keypad during the call. A blank string will be used if they didn&#39;t provide any input. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
