# OwnNumber

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | The unique identifier for the record. | [optional]
**account_id** | **string** | The unique identifier for the account. | [optional]
**workspace_id** | **string** | The unique identifier for the workspace. | [optional]
**user_id** | **string** | The unique identifier for the user. | [optional]
**phone_number** | **string** | The user&#39;s phone number. | [optional]
**country** | **string** | The country code of the phone number. | [optional]
**label** | **string** | A label for the phone number. | [optional]
**status** | **string** | The status of the phone number. | [optional]
**verified_timestamp** | **\DateTime** | The timestamp when the phone number was verified. | [optional]
**notified_timestamp** | **string** | The timestamp when the user was last notified about this number, if applicable. | [optional]
**is_nearing_expiration** | **bool** | Indicates whether the phone number verification is nearing its expiration date: - **true:** The verification was completed more than 11 months ago and will expire soon. You should re-verify your phone number to maintain uninterrupted service. - **false:** The verification is still valid and not approaching expiration. | [optional]
**created_timestamp** | **\DateTime** | The timestamp when the record was created. | [optional]
**updated_timestamp** | **\DateTime** | The timestamp when the record was last updated. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
