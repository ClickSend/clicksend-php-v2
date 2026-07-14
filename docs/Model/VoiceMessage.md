# VoiceMessage

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**date** | **string** | The date, if applicable. May be null; see also &#x60;date_added&#x60;. | [optional]
**date_added** | **int** | The Unix timestamp when the message was added. | [optional]
**list_id** | **string** | The ID of the list associated with the message, if applicable. | [optional]
**to** | **string** | The recipient&#39;s phone number. | [optional]
**to_type** | **string** | The type of recipient. | [optional]
**body** | **string** | The body of the message. | [optional]
**from** | **string** | The sender&#39;s phone number. | [optional]
**lang** | **string** | The language of the message. | [optional]
**voice** | **string** | The voice of the message. | [optional]
**schedule** | **string** | The timestamp when the message should be sent. Returned as a string since it may be an empty string when no schedule was set. | [optional]
**message_id** | **string** | The ID of the message. | [optional]
**message_parts** | **string** | The number of parts in the message. | [optional]
**message_price** | **string** | The price of the message. | [optional]
**custom_string** | **string** | The custom string of the message. | [optional]
**user_id** | **float** | The ID of the user. | [optional]
**subaccount_id** | **float** | The ID of the subaccount. | [optional]
**country** | **string** | The country code of the message. | [optional]
**require_input** | **float** | The require input of the message. | [optional]
**machine_detection** | **float** | The machine detection of the message. | [optional]
**machine_detected** | **float** | Flag indicating if an answering machine was detected. | [optional]
**digits** | **string** | The digits entered by the recipient, if any input was collected. | [optional]
**carrier** | **string** | The carrier of the recipient&#39;s phone number. | [optional]
**status_code** | **string** | The status code of the message. | [optional]
**status_text** | **string** | A human-readable description of the status. | [optional]
**status** | **string** | The status of the message. | [optional]
**_api_username** | **string** | The API username associated with the message. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
