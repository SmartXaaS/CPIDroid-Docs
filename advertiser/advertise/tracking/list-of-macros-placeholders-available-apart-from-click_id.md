# List of Macros / Placeholders available apart from {click\_id}

We are able to pass some additional macros/placeholders apart from **{click\_id}** which can be replaced with corresponding values and passed via tracking or redirect link.

We currently support only two additional macros that we populate on click-out:

* **{gaid}** - google advertising id
* **{idfa}** - apple advertising id
* **{pub\_id}** - first level publisher id
* **{sub\_id}** - second level publisher id (if available)

**Example:** _https://example.com/tracking.php?campaign\_id=XXXX\&click\_id=<mark style="color:red;">**{click\_id}**</mark>\&gaid=<mark style="color:red;background-color:red;">**{gaid}**</mark>\&pub\_id=<mark style="color:red;">**{pub\_id}**</mark>\&sub\_id=<mark style="color:red;">**{sub\_id}**</mark>_

You can use those to assign installs / in-app activity to specific publishers or sub-publishers and thus optimize campaign performance over time by eventually blacklisting non-performing sources.
