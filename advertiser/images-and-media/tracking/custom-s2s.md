# Custom S2S

#### **About Custom S2S**

Custom tracking is available for advanced users who need to integrate their own tracking solution, not pre-integrated with CPIDroid. Tracking Link and Postback URL both are the important things for Custom S2S Tracking to work properly.\


#### **Overview:**

* [Generating the Tracking Link](custom-s2s.md#h_01fedvwxkdt5pw4nb9qb6zaapb)
* [Preparing the Postback URL](custom-s2s.md#h_01fedy8x5ryvgw57e6fjtbxjwv)
* [Sending the Conversion Postback](custom-s2s.md#h_01fedy7vpts5166c9h7v07qc2x)

### Generating the Tracking Link <a href="#h_01fedvwxkdt5pw4nb9qb6zaapb" id="h_01fedvwxkdt5pw4nb9qb6zaapb"></a>

Tracking link help you to track the user who interacts (clicks) with the ads and takes the user to the advertised app in the App Store or Play Store.

* You will have to setup your own tracking link (via your own tracking solution) and it must carry the macro/placeholder **{click\_id}**, which is dynamically replaced with a generated click id we supply.
* You need to check with your tracking provider to generate a tracking link from your custom tracking software provider's dashboard.
* Your tracking link should must have a url data parameter to carry our {click\_id} macro. Usually, this parameter is called as Click ID or External ID by various tracking software providers.\
  &#xNAN;_&#x4E;ote: Some tracking system may not have a dedicated click id data parameter, but they should have alternative parameters to carry custom data which can be used instead such as "data", "var", "custom" and "sub" ..etc._
*   For example, if your click id data parameter is "clickid" then tracking link should look like:-\


    <pre><code><strong>https://example.com/tracking.php?campaign_id=abc123&#x26;clickid={click_id}
    </strong></code></pre>

    \
    _Note: Our system will generate & pass unique values on parameter "clickid" by replacing {click\_id} placeholder dynamically every time the tracking url is clicked by any user._\

* Your tracking system should catch the value of our {click\_id} and save it in their database, because if that click results into conversion later, it will have to send postback with same value.
* Our system can pass several data to your tracking url by making use of macros/placeholders we have available, kindly refer this guide : [List of Macros / Placeholders available apart from {click\_id}](https://thesmartware.zendesk.com/hc/en-us/articles/360026061891-List-of-Macros-Placeholders-available-apart-from-click-id-)&#x20;

Please note that you will have to enter your tracking link in the "Tracking Link" field given under "Select Tracking Method" box while creating the campaign.

### Preparing the Postback URL <a href="#h_01fedy8x5ryvgw57e6fjtbxjwv" id="h_01fedy8x5ryvgw57e6fjtbxjwv"></a>

You will get the default postback url while creating campaign but you may have to prepare them by adjusting the macro/placeholder as per your tracking system.

How to get your default Postback URL?

1. Please go to [https://app.cpidroid.com/postback?dashboard=advertiser](https://app.cpidroid.com/postback?dashboard=advertiser) (login required)
2. Copy your default Postback URL and paste/save it within your own tracking system.

Prepare your Install Postback URL:

*   If your tracking system's click id data macro/placeholder is {CLICKID} then Install Postback URL should look like below example:-\


    <pre><code><strong>https://track.cpidroid.com/install.php?click_id={CLICKID}&#x26;token=[TOKEN]
    </strong></code></pre>

Prepare your Event Postback URL:

* If your tracking system's click id data macro/placeholder is {CLICKID} then Event Postback URL should look like below example: \
  `https://track.cpidroid.com/event.php?click_id={CLICKID}&event_name=EVENT_NAME&token=[TOKEN]`

_Note: In case of CPA campaign, unique even name is required, you may hardcode it into the postback url on parameter "**event\_name"**_

### Sending the Conversion Postback <a href="#h_01fedy7vpts5166c9h7v07qc2x" id="h_01fedy7vpts5166c9h7v07qc2x"></a>

Postback URL help us to get notified about the user who completed the desired actions (conversions) after interacting with the ads.

* We will provide you with a postback URL. You will have to send conversion postbacks to our server on our postback URL after a successful conversion.
* We have two separate postback urls, Install Postback URL (for CPI campaigns) and Event Postback URL (for CPA campaigns) => Make sure to set correct postback url accordingly.
* You will have to prepare/configure our postback urls for your tracking system and enable your tracking system to send conversion postbacks to our postback url.
* Make sure to pass the unique value (same as we passed into your tracking link) of our click id on "click\_id" parameter into the postback url.

\*Make sure you contact us first to test and enable Custom S2S tracking for your account.

**FOR ADVANCED USER:**

How to develop your own custom tracking system for Android app?

* You can develop your own tracking url and pass our click id to your server like below example:-\
  `https://track.yourserver.com/click.php?network=cpidroid&click_id={click_id}`  \
  \
  You should be able to store click id, ip address and other details with the help of which you can do probabilistic attribution and send us postbacks accordingly.
* You can redirect users to play store and pass our click id through "referrer" URL parameter like below example:-\
  `https://play.google.com/store/apps/details?id=com.example.application&referrer={click_id}` \
  Learn more at [https://stackoverflow.com/questions/66205959/how-to-get-referrer-code-from-playstore-using-play-install-referrer-library](https://stackoverflow.com/questions/66205959/how-to-get-referrer-code-from-playstore-using-play-install-referrer-library)&#x20;
* You need to read the value of INSTALL\_REFERRER to grab the click id that was passed.\
  Learn more at [https://developer.android.com/google/play/installreferrer](https://developer.android.com/google/play/installreferrer)&#x20;
* Once you have the click id, you can send install postback to our postback url from within the app or maybe from your server.



<mark style="color:red;">**Risk Disclaimer for Affiliates/Agencies/Networks:-**</mark>

If you are an Affiliate/Agency/Network and going to setup custom s2s with us then you can try S2S but please be aware of a few things:-

* We are connected to quite a lot of networks already. This is specifically true for incent campaigns. In case we get the same offer from multiple sources we send traffic only to the source with the highest bid. This means there is a chance that campaigns of yours are not getting approved, if the bid is too low.
* We are monitoring conversion rate for these campaigns. In case CR is too low or any other issues arise, the campaign will get suspended.
* We don't assume liability for any KPIs that are reached for any campaign. We are able to optimize campaigns though.
* For CPI / CPA campaigns specifically, we'll need to make sure that\
  &#x20;\- Redirect links are always directing to the store and not to other pages.\
  &#x20;\- Campaigns get paused in case the daily cap is reached.\
  &#x20;\- The bid is reasonable for the targeted countries
* Learn more at [https://thesmartware.zendesk.com/hc/en-us/articles/115001401111-Can-I-use-custom-affiliate-tracking-redirect-link-](https://thesmartware.zendesk.com/hc/en-us/articles/115001401111-Can-I-use-custom-affiliate-tracking-redirect-link-)&#x20;

