# ViewSmsHistoryDataAllOfDataInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**direction** | **string** | It can either be in or out:   - **in** - You received a message. it has to do with inbound messages.   - **out** - You are sending a message. It has to do with outbound messages. | [optional]
**date** | **int** | The date you sent the message. It is in &lt;a href&#x3D;\&quot;http://help.clicksend.com/what-is-a-unix-timestamp\&quot; target&#x3D;\&quot;_blank\&quot;&gt;Unix format&lt;/a&gt;. | [optional]
**to** | **string** | The phone number of the recipient. It should be in &lt;a href&#x3D;\&quot;https://en.wikipedia.org/wiki/E.164\&quot; target&#x3D;\&quot;_blank\&quot;&gt;E.164 format&lt;/a&gt;. | [optional]
**body** | **string** | The message sent. | [optional]
**status** | **string** | The status of the SMS. It can either be:  - _Queued_ - _Completed_ - _Scheduled_ - _WaitApproval_ - _Failed_ - _Cancelled_ - _CancelledAfterReview_ - _Received_ - _Sent_  This parameter reflects the actual status of the SMS. It is based on the  status of the SMS sent from the &lt;a href&#x3D;\&quot;https://en.wikipedia.org/wiki/SMS_gateway\&quot; target&#x3D;\&quot;_blank\&quot;&gt;SMS gateway&lt;/a&gt;, which is different  from the [API status code](https://developers-dev.clicksend.net/docs/#status-codes). Visit &lt;a href&#x3D;\&quot;https://help.clicksend.com/article/8cc479qlbb-list-of-sms-gateway-error-codes\&quot; target&#x3D;\&quot;_blank\&quot;&gt;this page&lt;/a&gt; for more information. | [optional]
**from** | **string** | The sender of the message. | [optional]
**schedule** | **string** | The scheduled date of the message. It is in &lt;a href&#x3D;\&quot;http://help.clicksend.com/what-is-a-unix-timestamp\&quot; target&#x3D;\&quot;_blank\&quot;&gt;Unix format&lt;/a&gt;. | [optional]
**status_code** | **string** | The status code sent from the &lt;a href&#x3D;\&quot;https://en.wikipedia.org/wiki/SMS_gateway\&quot; target&#x3D;\&quot;_blank\&quot;&gt;SMS gateway&lt;/a&gt;. Visit &lt;a href&#x3D;\&quot;https://help.clicksend.com/article/8cc479qlbb-list-of-sms-gateway-error-codes\&quot; target&#x3D;\&quot;_blank\&quot;&gt;this page&lt;/a&gt; for more information. | [optional]
**status_text** | **string** | A message describing the _status_code_ of the operation. Visit &lt;a href&#x3D;\&quot;https://help.clicksend.com/article/8cc479qlbb-list-of-sms-gateway-error-codes\&quot; target&#x3D;\&quot;_blank\&quot;&gt;this page&lt;/a&gt; for more information. | [optional]
**error_code** | **string** | The error code of the operation. Visit &lt;a href&#x3D;\&quot;https://help.clicksend.com/article/8cc479qlbb-list-of-sms-gateway-error-codes\&quot; target&#x3D;\&quot;_blank\&quot;&gt;this page&lt;/a&gt; for more information. If no error occurred, the value is **null**. | [optional]
**error_text** | **string** | A message describing the _error_code_ of the operation. Visit &lt;a href&#x3D;\&quot;https://help.clicksend.com/article/8cc479qlbb-list-of-sms-gateway-error-codes\&quot; target&#x3D;\&quot;_blank\&quot;&gt;this page&lt;/a&gt; for more information. If no error occurred, the value is **null**. | [optional]
**message_id** | **string** | The generated ID of the message. | [optional]
**message_parts** | **int** | The number of parts the message was broken into. To look at how many parts your message is broken down into, use the &lt;a href&#x3D;\&quot;http://smscharactercount.com/\&quot; target&#x3D;\&quot;_blank\&quot;&gt;&lt;strong&gt;SMS Character Count&lt;/strong&gt;&lt;/a&gt;. | [optional]
**message_price** | **string** | The price of this message. This depends on the total number of parts of the message. | [optional]
**from_email** | **string** | The email address to which replies should be emailed to. If omitted, the reply will be emailed back to the user who sent the outgoing SMS | [optional]
**list_id** | **string** | The _list_id_ of the contact list the message was sent to. This parameter will have a **null** value if you didn’t send to a list in the request. | [optional]
**custom_string** | **string** | A note that was included with the outgoing SMS. If no note was included, the value is **null**. | [optional]
**contact_id** | **string** | This is the ID of the contact. This parameter will have a **null** value if you didn’t provide a _contact_id_ in the request. | [optional]
**user_id** | **int** | The unique user ID of the sender. | [optional]
**subaccount_id** | **int** | The sub-account of the user. A user can have multiple sub-accounts. | [optional]
**country** | **string** | The country of the recipient in two-letter format (e.g. US, UK, AU, NZ, etc). | [optional]
**carrier** | **string** | The phone carrier of the recipient. | [optional]
**first_name** | **string** | The first name of the recipient. The name will appear if you sent the message to a contact from a contact list. If you are sending directly to a phone number, the value will be **null**. | [optional]
**last_name** | **string** | The last name of the recipient. The name will appear if you sent the message to a contact from a contact list. If you are sending directly to a phone number, the value will be **null**. | [optional]
**_api_username** | **string** | The username of the SMS sender. This can be a &lt;a href&#x3D;\&quot;https://dashboard.clicksend.com/account/subaccounts\&quot; target&#x3D;\&quot;_blank\&quot;&gt;sub-account&lt;/a&gt;. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
