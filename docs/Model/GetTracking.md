# GetTracking

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**total** | **float** | Total number of short URLs associated with the long URL ID | [optional]
**per_page** | **float** | The limit of tracking data per page | [optional]
**current_page_size** | **float** | The number of data in the current page | [optional]
**prev_page_url** | **string** | Link to the previous page. This attribute will not be present if there is no previous page. | [optional]
**next_page_url** | **string** | Link to the next page. This attribute will not be present if there is no next page. | [optional]
**data** | [**\ClickSend\Model\GetTrackingDataInner[]**](GetTrackingDataInner.md) | Tracking data of the short URLs associated with the specified long URL ID. Note that only the data from the most recent click of the recipient (country, region, device, browser, and os) is recorded. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
