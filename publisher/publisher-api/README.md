---
description: Publisher API - Documentation Guide (v1.1)
icon: rectangle-code
---

# Publisher API

**Overview:**

* [Offer Get API:](./#h_01gt9b9gcscfme8jvdy8qf1dv8)
* [Offerwall Get API:](./#h_01gt9ba3espjk1rxb4xj02mxsb)

&#x20;

### Offer Get API: <a href="#h_01gt9b9gcscfme8jvdy8qf1dv8" id="h_01gt9b9gcscfme8jvdy8qf1dv8"></a>

| **API Name** | **End Point**                                                                       | **API Doc**                                                                                                                                                                                      |
| ------------ | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Offer Get    | https://api.cpidroid.com/offer/get?apikey=\[APIKEY]\&placement\_id=\[PLACEMENT\_ID] | [https://documenter.getpostman.com/view/6925801/2s93CNPEAt#fafd80de-1e4c-4d0f-a615-1ae7fff65237](https://documenter.getpostman.com/view/6925801/2s93CNPEAt#fafd80de-1e4c-4d0f-a615-1ae7fff65237) |

_Note: Grab your API keys from_ [_https://app.cpidroid.com/account/api?dashboard=publisher_](https://app.cpidroid.com/account/api?dashboard=publisher)&#x20;

Sample Code \[PHP]:

```
<?php 
$apikey = 'YOUR_APIKEY';
$placement_id = 'PLACEMENT_ID';

$offers = file_get_contents('https://api.cpidroid.com/offer/get?apikey='.$apikey.'&placement_id='.$placement_id);
$offers = json_decode($offers, true);

if($offers['status'] == 'success' && $offers['count'] > 0){
    $offers = $offers['data'];
    print_r($offers);
}
?>
```

&#x20;

### Offerwall Get API: <a href="#h_01gt9ba3espjk1rxb4xj02mxsb" id="h_01gt9ba3espjk1rxb4xj02mxsb"></a>

| **API Name**  | **End Point**                                                                                                                        | **API Doc**                                                                                                                                                                                       |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Offerwall Get | https://api.cpidroid.com/offerwall/get?apikey=\[APIKEY]\&placement\_id=\[PLACEMENT\_ID]\&uid=\[USER\_IDENTIFIER]\&country=\[COUNTRY] | [https://documenter.getpostman.com/view/6925801/2s93CNPEAt#1b842b32-4758-4ea1-be6b-6da8e3b103fd](https://documenter.getpostman.com/view/6925801/2s93CNPEAt#1b842b32-4758-4ea1-be6b-6da8e3b103fd)  |

_Note: Grab your API keys from_ [_https://app.cpidroid.com/account/api?dashboard=publisher_](https://app.cpidroid.com/account/api?dashboard=publisher)&#x20;
