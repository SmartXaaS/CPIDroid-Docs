# Campaign Add

#### API Endpoint

**POST** `https://api.cpidroid.com/campaign/add?platform=android`

#### Authorization

To access the API, a valid API key is required for authentication. Ensure you have included the API key in your request header.

| Key    | Value   |
| ------ | ------- |
| apikey | ••••••• |

#### Params

When making a request, ensure the following parameters are passed:

| Parameter | Required | Description           |
| --------- | -------- | --------------------- |
| platform  | android  | android or ios or web |

#### Body (form-data)

When sending data in the body of the request, the fields listed below should be included as form-data:

| Field         | Value                                                                                                                                                  | Description                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| app\_url      | [https://play.google.com/store/apps/details?id=com.TheSmartWare.JungleRaja](https://play.google.com/store/apps/details?id=com.TheSmartWare.JungleRaja) | play store or app store url                            |
| traffic       | incent                                                                                                                                                 |                                                        |
| type          | cpi.standard                                                                                                                                           | cpc.standard or cpi.standard                           |
| budget        | 100                                                                                                                                                    |                                                        |
| bid           | 0.1                                                                                                                                                    |                                                        |
| cap           | 1000000                                                                                                                                                | cap on conversions per day                             |
| tracker       | custom\_s2s                                                                                                                                            |                                                        |
| redirect\_url |                                                                                                                                                        | tracking url, if applicable                            |
| country       |                                                                                                                                                        | optional, pass country\[] array for multiple countries |

#### Example Request

The following example demonstrates how to structure a curl request to the API endpoint:

```bash
curl --location 'https://api.cpidroid.com/campaign/add?platform=android' \
--form 'app_url="https://play.google.com/store/apps/details?id=com.TheSmartWare.JungleRaja"' \
--form 'traffic="incent"' \
--form 'type="cpi.standard"' \
--form 'budget="100"' \
--form 'bid="0.1"' \
--form 'cap="1000000"' \
--form 'tracker="custom_s2s"' \
--form 'redirect_url=""' \
--form 'country=""'
```

#### Example Response

In case of an error, the API would respond with a detailed error message as below:

```json
{
  "status": "error",
  "message": "Error",
  "error": [
    "Campaign budget ($100) should NOT be greater than USD Balance ($0.00000). Kindly <a href=\"#DepositFundsModal\" data-toggle=\"modal\">add sufficient funds in your USD Balance</a>.",
    "Tracking Link: Kindly enter a valid tracking link for chosen tracking provider (custom_s2s). It should be a URL.",
    "Your custom_s2s tracking link is invalid. Kindly refer above errors for more details."
  ]
}
```

#### Notes

* Ensure that your API key is active and has the necessary permissions.
* Double-check the provided URLs for legality and activeness.
* Monitor your daily cap to avoid exceeding limitations.
