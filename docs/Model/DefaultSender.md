# DefaultSender

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** | ID of the default sender. |
**user_id** | **int** | User ID from the version 3 system. |
**subaccount_id** | **int** | Subaccount ID from version 3. |
**country_code** | **string** | ISO 3166-1 alpha-2 formatted country code. |
**product_type** | **string** | Type of product for which the setting is applied. |
**default_sender_strategies** | [**\ClickSend\Model\DefaultSenderDefaultSenderStrategiesInner[]**](DefaultSenderDefaultSenderStrategiesInner.md) | Default sender strategies. Must contain 1 or more objects. |
**status** | **string** | Overall status of the default sender. |
**created_timestamp** | **string** | Timestamp of when the default sender was created. Must be in ISO 8601 format. |
**updated_timestamp** | **string** | Timestamp of the last update to the default sender. Must be in ISO 8601 format. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
