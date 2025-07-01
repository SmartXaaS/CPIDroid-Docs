# Web

**About Offerwall Monetization:**

* You can monetize your non-paying users with our incent offerwall
* Kindly go to [https://wall.cpidroid.com/offer/69o8-1-3ghh?uid=USER\_IDENTIFIER](https://wall.cpidroid.com/offer/69o8-1-3ghh?uid=USER_IDENTIFIER) to experience it live.
* Once you become publisher, you can get you own unique offerwall link.
* Your end users will have to complete tasks / surveys / offers in CPIDroid offerwall and you will get payouts, you can pass on a part of that to the end user as some kind of reward.
* You can setup postbacks to get server to server callbacks when user complete a task, to automate rewarding your end users.

**Creating Offerwall Placement:-**

* Getting Started with Placements : [https://thesmartware.zendesk.com/hc/en-us/articles/15591044527257-Getting-Started-with-Placements](https://thesmartware.zendesk.com/hc/en-us/articles/15591044527257-Getting-Started-with-Placements)

**Preparing your Offerwall URL:-**

*   The URL template for our web offerwall looks like this:\


    ```
    https://wall.cpidroid.com/offer/[PLACEMENT_ID]?uid=USER_IDENTIFIER&gaid={gaid}&idfa={idfa}
    ```
*   URL Parameters:

    | **Parameter**    |   | **Description**                                                                                                                                                                                                 |
    | ---------------- | - | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | \[PLACEMENT\_ID] |   | Replace it with the placement id, find it at [https://app.cpidroid.com/placement/manage?dashboard=publisher](https://app.cpidroid.com/placement/manage?dashboard=publisher)                                     |
    | {gaid}           |   | <p>Google Advertising ID (GAID)<br><em>Resource:</em> <a href="https://developer.android.com/training/articles/ad-id"><em>How to fetch GAID in Android?</em></a> </p>                                           |
    | {idfa}           |   | <p>Apple Advertising ID (IDFA)<br><em>Resource:</em> <a href="https://developer.apple.com/documentation/adsupport/asidentifiermanager/1614151-advertisingidentifier"><em>How to fetch IDFA in iOS?</em></a></p> |
    | USER\_IDENTIFIER |   | Replace it with a unique identifier per user.                                                                                                                                                                   |

    &#x20;
*   Example: Usage in Android WebView\
    If you're developing an app built upon native Android components, you can load the offerwall like this:-\
    **layout.xml:**\


    ```
    <WebView
    	android:id="@+id/myWebViewId"
    	android:layout_width="match_parent"
    	android:layout_height="match_parent"/>
    ```

    \
    **MyOfferwall.java:**\


    ```
    ...
    String offerwallUrl = "https://wall.cpidroid.com/offer/[PLACEMENT_ID]?gaid="+adInfo.getId()+"&gaid_limited="+adInfo.isLimitAdTrackingEnabled()+"&uid=USER_IDENTIFIER";
    // NOTE: check this for information on how to obtain the GAID -> https://developer.android.com/training/articles/ad-id

    WebView myWebView = (WebView) findViewById(R.id.myWebViewId);
    myWebView.getSettings().setJavaScriptEnabled(true);
    myWebView.setWebViewClient(new WebViewClient() {
        @Override
        public boolean shouldOverrideUrlLoading(WebView view, String url) {
            if( URLUtil.isNetworkUrl(url) ) {
                return false;
            }
            try {
                Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
                startActivity( intent );
            } catch (Exception e) {
                return false;
            }
            return true;
        }
    });
    myWebView.loadUrl(offerwallUrl);
    ```

    \
    **Attention:** Make sure you don't forget to enable Javascript for your WebView!

**Adding your Callback URL:-**

* You can configure a conversion callback URL from [publisher dashboard](https://app.cpidroid.com/?dashboard=publisher)
* While editing a placement at [https://app.cpidroid.com/placement/manage](https://app.cpidroid.com/placement/manage)
* You should be able to see option to add a callback url.

**How to Prepare your Postback URL?**

*   Here is an example of how an ideal postbacks url should look:-

    ```
    https://your-server.com/callback?network=cpidroid&offer_id={offer_id}&payout_vc={payout_vc}&uid=USER_IDENTIFIER&payout_usd={payout_usd}
    ```
*   A typical conversion callback sent by our server will look like this:-

    ```
    https://your-server.com/callback?network=cpidroid&offer_id=123456&payout_vc=1500&uid=username&payout_usd=1.5
    ```



_Note: This assumes you set uid to **username** in the original Offerwall URL for that user, the currency conversion rate in your placement was 1000 per $1 and the user completed an offer with a $1.5 payout._\
\
<mark style="color:red;">**Important:**</mark> <mark style="color:red;"></mark><mark style="color:red;">Your server must always reply with an</mark> <mark style="color:red;"></mark><mark style="color:red;">**HTTP 200 status code**</mark> <mark style="color:red;"></mark><mark style="color:red;">to our callbacks. Otherwise we will assume something went wrong with your server and send an automated email alert to you with technical details. You can always re-send postback from your publisher dashboard.</mark>

**Available Macros for Callback URLs:-**&#x20;

| **Variable**  | **Type** | **Description**                       |
| ------------- | -------- | ------------------------------------- |
| {offer\_id}   |          | Offer ID                              |
| {offer\_name} |          | Offer Name                            |
| {payout\_vc}  |          | Payout in equivalent Virtual Currency |
| {payout\_usd} |          | Payout in equivalent USD Currency     |
| {uid}         |          | USER\_IDENTIFIER                      |
| {sub\_id}     |          | SUB\_ID                               |
| {ip}          |          | User IP                               |
| {txn\_id}     |          | Unique Conversion Transaction ID      |

