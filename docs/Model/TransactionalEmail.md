# TransactionalEmail

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**user_id** | **int** | The ID of the user. | [optional]
**subaccount_id** | **int** | The ID of the subaccount. | [optional]
**from_email_address_id** | **int** | The ID of the from email address. | [optional]
**from_name** | **string** | The name of the sender. | [optional]
**to** | [**\ClickSend\Model\SendEmailRequestToInner[]**](SendEmailRequestToInner.md) |  | [optional]
**cc** | [**\ClickSend\Model\SendEmailRequestToInner[]**](SendEmailRequestToInner.md) |  | [optional]
**bcc** | [**\ClickSend\Model\SendEmailRequestToInner[]**](SendEmailRequestToInner.md) |  | [optional]
**subject** | **string** | The subject of the email. | [optional]
**body** | **string** | The HTML body of the email. | [optional]
**body_plain_text** | **string** | The plain text body of the email. | [optional]
**schedule** | **int** | The timestamp indicating the scheduled time of the email. | [optional]
**message_id** | **string** | The ID of the email message. | [optional]
**status** | **string** | The status of the email. | [optional]
**status_text** | **string** | The text description of the email status. | [optional]
**soft_bounce_count** | **int** | The count of soft bounces. | [optional]
**hard_bounce_count** | **int** | The count of hard bounces. | [optional]
**price** | **string** | The price of the email. | [optional]
**date_added** | **int** | The timestamp indicating when the email was added. | [optional]
**custom_string** | **string** | A custom string. | [optional]
**_attachments** | [**\ClickSend\Model\Attachment[]**](Attachment.md) |  | [optional]
**_currency** | [**\ClickSend\Model\Currency**](Currency.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
