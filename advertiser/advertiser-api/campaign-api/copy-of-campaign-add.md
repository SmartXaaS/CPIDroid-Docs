# Copy of Campaign Add

### POST /campaign/add

#### Endpoint

`https://api.cpidroid.com/campaign/add?platform=android`

Send a POST request to this endpoint to create a campaign.

#### Authorization

*   **API Key**:

    * **Key**: `apikey`
    * **Value**: `•••••••`

    #### Parameters

    * **platform**: `android`\
      Options: `android`, `ios`, `web`

    #### Body (form-data)

    * **app\_url**: `https://play.google.com/store/apps/details?id=com.TheSmartWare.JungleRaja`\
      Provide the Play Store or App Store URL.
    * **traffic**: `incent`
    * **type**: `cpi.standard`\
      Options: `cpc.standard`, `cpi.standard`
    * **budget**: `100`
    * **bid**: `0.1`
    * **cap**: `1000000`\
      Daily conversion cap.
    * **tracker**: `custom_s2s`
    * **redirect\_url**: Tracking URL, if applicable
    * **country**: Optional, specify `country[]` array for multiple countries

    #### Request Example

    ```php
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

    #### Response Example

    ```json
    {
      "status": "error",
      "message": "Error",
      "error": [
        "Campaign budget ($100) should NOT be greater than USD Balance ($0.00000). Kindly <a href=\"#DepositFundsModal\" data-toggle=\"modal\">add sufficient funds</a> in your USD Balance",
        "Tracking Link : Kindly enter a valid tracking link for choosen tracking provider (custom_s2s). It should be an URL.",
        "Your custom_s2s tracking link is invalid. Kindly refer above errors for more details."
      ]
    }
    ```
