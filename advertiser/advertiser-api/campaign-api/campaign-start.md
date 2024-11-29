# Campaign Start

#### API Endpoint

**POST** `https://api.cpidroid.com/campaign/start?campaign_id=123456`

#### Authorization

To access the API, a valid API key is required for authentication. Ensure you have included the API key in your request header.

| Key    | Value   |
| ------ | ------- |
| apikey | ••••••• |

#### Params

When making a request, ensure the following parameters are passed:

| Parameter    | Required |
| ------------ | -------- |
| campaign\_id | 123456   |

#### Example Request

The following example demonstrates how to structure a curl request to the API endpoint:

```bash
curl --location 'https://api.cpidroid.com/campaign/start?campaign_id=25539'
```

#### Example Response

In case of an error, the API would respond with a detailed error message as below:

```json
{
  "status": "success",
  "message": "Success",
  "success": [
    "Campaign #MH-25539 is live (status=running)."
  ]
}
```

#### Notes

* Ensure that your API key is active and has the necessary permissions.
* Double-check the provided URLs for legality and activeness.
* Monitor your daily cap to avoid exceeding limitations.
