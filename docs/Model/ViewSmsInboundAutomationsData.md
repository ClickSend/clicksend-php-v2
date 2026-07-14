# ViewSmsInboundAutomationsData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**total** | **int** | The total number of items available for viewing. | [optional]
**per_page** | **int** | The number of items returned per page. This is specified in the limit parameter. You can have 100 items at maximum, and 15 at minimum. | [optional]
**current_page** | **int** | The current page number. | [optional]
**last_page** | **int** | The last page number. | [optional]
**next_page_url** | **string** | A URL of the next page. It will return **null** if there’s no next page. | [optional]
**prev_page_url** | **string** | A URL of the previous page. It will return **null** if there’s no previous page. | [optional]
**from** | **int** | The number of the first result in the current page. | [optional]
**to** | **int** | The number of the last result in the current page. | [optional]
**first_page_url** | **string** | The URL of the first page of records. | [optional]
**last_page_url** | **string** | The URL of the last page of records. | [optional]
**path** | **string** | The base URL path used to build pagination links. | [optional]
**links** | [**\ClickSend\Model\ViewListsDataLinksInner[]**](ViewListsDataLinksInner.md) | The list of pagination links. | [optional]
**data** | [**\ClickSend\Model\SmsInboundRule[]**](SmsInboundRule.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
