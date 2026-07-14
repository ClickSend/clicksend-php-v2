# CalculateSmsPriceData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**total_price** | **float** | The total price of sending the messages. Visit [this page](/#status-codes) for more information. | [optional]
**total_count** | **int** | The total number of messages sent from the request. | [optional]
**queued_count** | **int** | The messages will be put in a queue if it goes through the validation process. The validation process checks whether the **Sender ID** is registered or not. Some countries don&#39;t require messages to go through the validation process.  Messages scheduled to be sent right away will be sent immediately. If not, it will be queued. | [optional]
**messages** | [**\ClickSend\Model\Sms[]**](Sms.md) | The parameters related to messages. | [optional]
**_currency** | [**\ClickSend\Model\Currency**](Currency.md) |  | [optional]
**_summary** | [**\ClickSend\Model\CalculateSmsPriceDataSummary**](CalculateSmsPriceDataSummary.md) |  | [optional]
**blocked_count** | **int** | The number of messages unable to be sent. This is often caused by:  - Receipient’s country not enabled for global sending.      - Sender ID resitriction.      - Number registration restrcition. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
