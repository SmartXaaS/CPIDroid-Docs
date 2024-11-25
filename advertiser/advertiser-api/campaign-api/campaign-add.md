# Campaign Add

#### POST Request to Create Campaign

To create a campaign, send a POST request to the following API endpoint:

```
https://api.cpidroid.com/campaign/add?platform=android
```

**Authorization**

* **Method:** API Key
* **Key:** apikey
* **Value:** •••••••

**Parameters**

*   **platform:** `android`

    * Options: `android`, `ios`, `web`

    **Body Parameters**

    * **Type:** `formdata`
      * **app\_url:**
        * `https://play.google.com/store/apps/details?id=com.TheSmartWare.JungleRaja`
        * Supported: Play Store or App Store URL
      * **traffic:** `incent`
      * **type:** `cpi.standard`
        * Options: `cpc.standard`, `cpi.standard`
      * **budget:** `100`
      * **bid:** `0.1`
      * **cap:** `1000000`
        * Cap on conversions per day
      * **tracker:** `custom_s2s`
      * **redirect\_url:** tracking URL, if applicable
      * **country:** Optional, pass `country[]` array for multiple countries
