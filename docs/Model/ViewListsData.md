# ViewListsData

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**total** | **int** | The total number of contacts in the list. | [optional]
**per_page** | **int** | The number of contacts returned per page. | [optional]
**current_page** | **int** | The current page number. | [optional]
**last_page** | **int** | The total number of pages. | [optional]
**next_page_url** | **string** | The URL of the next page of contacts. | [optional]
**prev_page_url** | **string** | The URL of the previous page of contacts. | [optional]
**from** | **int** | The number of the first contact on the current page. | [optional]
**to** | **int** | The number of the last contact on the current page. | [optional]
**first_page_url** | **string** | The URL of the first page of records. | [optional]
**last_page_url** | **string** | The URL of the last page of records. | [optional]
**path** | **string** | The base URL path used to build pagination links. | [optional]
**links** | [**\ClickSend\Model\ViewListsDataLinksInner[]**](ViewListsDataLinksInner.md) | The list of pagination links. | [optional]
**data** | [**\ClickSend\Model\ContactList[]**](ContactList.md) | The contacts in the list. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
