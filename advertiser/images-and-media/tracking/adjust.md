# Adjust

**About Adjust Tracking / SDK**\
Adjust is a 3rd party tracking solution which provides tracking SDK and the purpose of tracking SDK is to track installs or conversions, report it to Adjust data center, then they verify the same and send a conversion postback to our server.

If you integrated the Adjust tracking SDK into your app, you can use Adjust as tracking solution. This allows you to rely on their reporting and anti-fraud measures. Additionally, you can create and run CPA campaigns in this setup. Please keep in mind that Adjust will charge you an additional fee per attribution for their services.&#x20;

New to Adjust? Kindly refer this official step by step guide by Adjust => [Getting Started: Step-by-Step](https://docs.adjust.com/en/getting-started/)

**Overview:**

1. [Integrate Adjust SDK:](adjust.md#h_01eqfh5c30ncx0c4cj8zkpdpq7)
2. [Initialize SDK & Test Integration:](adjust.md#h_01ex23b9q71swqry0798545av2)
3. [Activate Tracking Link for CPIDroid:](adjust.md#h_01eqfh5gm986h314ds894yrtf5)
4. [Enable Install/Event Postbacks:](adjust.md#h_01eqfh5n21m4hm3m87hv8p2gc2)

### 1. Integrate Adjust SDK: <a href="#h_01eqfh5c30ncx0c4cj8zkpdpq7" id="h_01eqfh5c30ncx0c4cj8zkpdpq7"></a>

You may need to integrate Adjust tracking SDK which is required for iOS CPI campaigns and you can learn more about it at [https://www.adjust.com](https://www.adjust.com/) or refer the official articles from Adjust help center as given below:-

* [Adjust SDK Integration - Android](https://github.com/adjust/android_sdk#summary)
* [Adjust SDK Integration - iOS](https://github.com/adjust/ios_sdk#summary)\
  &#x20;\- ATT Prompt : [https://help.adjust.com/en/article/app-tracking-transparency-att-framework](https://help.adjust.com/en/article/app-tracking-transparency-att-framework) \
  &#x20;\- Advanced Privacy : [https://help.adjust.com/en/article/attribution-privacy-models](https://help.adjust.com/en/article/attribution-privacy-models)&#x20;

### 2. Initialize SDK & Test Integration: <a href="#h_01ex23b9q71swqry0798545av2" id="h_01ex23b9q71swqry0798545av2"></a>

<mark style="color:red;">\*It is highly recommended that you initialize the SDK and test the integration beforehand.</mark>

### 3. Activate Tracking Link for CPIDroid: <a href="#h_01eqfh5gm986h314ds894yrtf5" id="h_01eqfh5gm986h314ds894yrtf5"></a>

* [http://help.adjust.com/tracking/attribution/tracker-urls/basic-tracker-setup](http://help.adjust.com/tracking/attribution/tracker-urls/basic-tracker-setup)
* **INDIA** : Kindly note that Indian Government has blocked adjust.com link nation wide and hence adjust.com tracking link will not work properly in India. Kindly refer this guide to run Adjust campaign in India => [https://help.adjust.com/en/article/how-to-run-campaigns-in-india](https://help.adjust.com/en/article/how-to-run-campaigns-in-india)&#x20;

### 4. Enable Install/Event Postbacks: <a href="#h_01eqfh5n21m4hm3m87hv8p2gc2" id="h_01eqfh5n21m4hm3m87hv8p2gc2"></a>

Our platform will automatically append our postback url into the tracking link by adding parameter "install\_callback" or "event\_callback\_123456"

&#x20;

**Need Extended Help with Adjust?**

Adjust is 3rd party and for extended support, you may refer their:

* Help Center : [https://docs.adjust.com/en/](https://docs.adjust.com/en/) or
* Simply contact their professional support team ([support@adjust.com](mailto:support@adjust.com)) for real help and guidance.

&#x20;

&#x20;

**Useful Information by Adjust for Advanced Users:**

Adjust uses a dynamic approach, so rather than having callback URLs hardcoded in their system, they give us more flexibility by allowing us to dynamically append our callback URL to the client's tracker URL. To create a customized tracking link with Adjust, please follow the instructions below.\
\
In a few easy steps, we will be able to create the final click URL for the campaign. To complete the setup, please refer to their partner tool which you’ll find here: [https://partners.adjust.com](https://partners.adjust.com/) \
\
The first field - ‘Enter your links’

* Enter the Adjust tracker URLs your clients have given you. You can also use our test URL: [https://app.adjust.com/cbtest](https://app.adjust.com/cbtest) (cbtest is our test token, which you can use if you don't have a tracker from a client) &#x20;
* Please make sure there are no extra spaces or blank lines.

The second field - ‘Your callbacks’

* Under the "Install" field, enter your complete callback URL including all of the parameters you require. &#x20;
* To complete the data you receive from our side, you can make use of this list of parameters (here) \[[https://partners.adjust.com/placeholders/](https://partners.adjust.com/placeholders/)]. &#x20;
* An example of a callback can look like this: [https://www.url.com\&idfa={idfa}\&click\_id={click\_id}](http://get.adjust-news.com/DGmb00N0ZAs00604Nd0t0su) &#x20;
* Make sure there are no extra spaces or blank lines.

The fourth field - ‘Generated URLs’

* Here you can find the final URL to run through your servers. &#x20;
* In our example, it's: [https://app.adjust.com/cbtest?install\_callback=https%3A%2F%2Fwww.url.com%26idfa%3D{idfa}%26click\_id%3D{click\_id}](https://app.adjust.com/cbtest?install_callback=https%3A%2F%2Fwww.url.com%26idfa%3D%7Bidfa%7D%26click_id%3D%7Bclick_id%7D)

Run the link through your servers, and use the output as a final link for customers to click on. Test the final link on a fresh device, a device upon which the app has not been installed yet. If you don’t have a fresh device, you can send us your device ID and we will flush it from our servers.\
\
If you need event/session callbacks, it works in the same way as install callbacks. You just use our event\_callback or session\_callback parameter to append your callback URL. With this format, you'll get a callback for all events. If you wish to track only a specific event, your client will provide you with a specific event token, for example 123456.\
\
Event callbacks:

[https://app.adjust.com/cbtest?install\_callback=https%3A%2F%2Fwww.url.com%26idfa%3D{idfa}%26click\_id%3D{click\_id}\&event\_callback\_123456=https%3A%2F%2Fwww.url.com%26idfa%3D{idfa}%26click\_id%3D{click\_id}](https://app.adjust.com/cbtest?install_callback=https%3A%2F%2Fwww.url.com%26idfa%3D%7Bidfa%7D%26click_id%3D%7Bclick_id%7D\&event_callback_123456=https%3A%2F%2Fwww.url.com%26idfa%3D%7Bidfa%7D%26click_id%3D%7Bclick_id%7D)\
\
Session callbacks:

[https://app.adjust.com/cbtest?install\_callback=https%3A%2F%2Fwww.url.com%26idfa%3D{idfa}%26click\_id%3D{click\_id}\&session\_callback=https%3A%2F%2Fwww.url.com%26idfa%3D{idfa}%26click\_id%3D{click\_id}](https://app.adjust.com/cbtest?install_callback=https%3A%2F%2Fwww.url.com%26idfa%3D%7Bidfa%7D%26click_id%3D%7Bclick_id%7D\&session_callback=https%3A%2F%2Fwww.url.com%26idfa%3D%7Bidfa%7D%26click_id%3D%7Bclick_id%7D)
