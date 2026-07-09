# MarkSpecificInboundSmsMessageAsRead

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**http_code** | **int** | The HTTP code of the response. Visit [this page](/#status-codes) for more information. | [optional]
**response_code** | **string** | The response code of the operation. Visit [this page](/#status-codes) for more information. | [optional]
**response_msg** | **string** | A message describing the outcome of the operation. | [optional]
**data** | **int** | The number of SMS marked as read.  If you have multiple inbound rules set to POLL, you will receive the inbound message multiple times. Reading it will mark all those messages as read. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
