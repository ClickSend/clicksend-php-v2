# GetTrackingDataInner

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**open_count** | **float** | Number of times the short URL was opened | [optional]
**date_opened** | **float** | Date in unix seconds when the short URL was first opened. Null if the short URL was never opened. | [optional]
**user_geo_country** | **string** | Country where the recipient is located when the short URL was opened. Null if the short URL was never opened. | [optional]
**user_geo_region** | **string** | Geographical region where the recipient is located when the short URL was opened. Null if the short URL was never opened. | [optional]
**user_device** | **string** | Deviced used by the recipient to open the short URL. Null if the short URL was never opened. | [optional]
**user_browser** | **string** | Browser used by the recipient to open the short URL. Null if the short URL was never opened. | [optional]
**user_os** | **string** | Opearating system used by the recipient to open the short URL. Null if the short URL was never opened. | [optional]
**contact** | [**\ClickSend\Model\GetTrackingDataInnerContact**](GetTrackingDataInnerContact.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
