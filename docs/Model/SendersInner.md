# SendersInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**recipient_country_code** | **string** | Recipient ISO country code |
**sender_id** | **string** | The sender ID must be either an alpha tag or a phone number. It is a required field unless the sender type is a &#x60;shared_longcode&#x60;.   If the sender ID is an **alpha tag**, it must be between 3 and 11 characters long and contains only letters, numbers, and pluses. | [optional]
**sender_type** | **string** | The type of sender ID, it only supports &#x60;shared_longcode&#x60; at the moment. | [optional]
**sender_country_code** | **string** | The ISO 3166-1 alpha-2 country code that identifies the country associated with the sender’s number in a shared pool. This is affected only when &#x60;sender_type&#x60; is set to &#x60;shared_longcode&#x60; to determine the appropriate number based on the sender’s geographic location. If this field is not provided or left empty, it will default to the recipient&#39;s country code. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
