---
description: Common data collection and integration questions and issues.
seo-description: Common data collection and integration questions and issues.
seo-title: Data Collection and Product Integration FAQ
solution: Audience Manager
title: Data Collection and Product Integration FAQ
uuid: fa8e79f4-99cb-41fd-8a85-d4f92d03c7a5
---

# Data Collection and Product Integration FAQ{#data-collection-and-product-integration-faq}

Common data collection and integration questions and issues.

<br>&nbsp;

<!-- 

faq_data_collection_integration.xml

 -->

**How can I differentiate inbound traffic from [!UICONTROL DCS] traffic in [!UICONTROL DCS] log file exports?**

Traits onboarded via [!UICONTROL Inbound] are populated by [!UICONTROL Inbound] the same way they get populated by [!UICONTROL DCS]. There are a few different ways to tell that traffic came from [!UICONTROL Inbound]:

* Remote IP will be set to 68.67.173.18
* DomainID will be set to 5325
* Region will be set to 0

<br>&nbsp;

**Can you provide me with a list of IP addresses I can whitelist for dpm.demdex.net?**

Unfortunately, we cannot. These IPs are assigned dynamically, by geographic region, through [!DNL Amazon Web Services]. As a result, [!DNL Audience Manager] does not control the range of IPs that can be assigned to this address.

<br>&nbsp;

**Can you provide me with an IP address I can whitelist for your inbound and outbound FTP server?**

Yes, see below.

Item| Address |
---------|----------|
 ftp-in.demdex.com | 54.225.117.163 |
 ftp-out.demdex.com | 23.23.188.76 |

<br>&nbsp;

**What are the code placement and page load requirements for a [!UICONTROL DIL]/[!DNL Analytics] Data Integration?**

To bring [!DNL Analytics] data into [!DNL Audience Manager], load [!UICONTROL DIL] after the `s_code` module but *before* the `s.t()` function. For example, place your code, or make sure it loads, in this order:

1. [!DNL Analytics] `s_code`

2. [!DNL Audience Manager] [!UICONTROL DIL] module

3. [!DNL Analytics] `s.t()` function

As a best practice, set up your [!DNL Audience Manager]- [!DNL Analytics] integration with either of these 2 methods:

* Put [!UICONTROL DIL] directly in the `s_code`.

* Serve [!UICONTROL DIL] and the `s_code` through [!DNL Adobe Launch] or [!DNL Adobe DTM].

See [Data Integration Library (DIL) API](../dil/dil-overview.md).

<br>&nbsp;

**Why are my [!DNL Analytics] variables missing from an [!DNL Audience Manager] event call?**

This usually happens when:

* You serve [!UICONTROL DIL] through a tag management system that loads it asynchronously with other code elements on the page. 
* The `s.t()` function loads before [!UICONTROL DIL].

<br>&nbsp;

**What versions of [!DNL Analytics] work with [!UICONTROL DIL]?**

You must use [!DNL Analytics] version 20.2 (or higher) and the [!DNL Adobe AppMeasurement AS] library version 3.5.2 (or higher) to work with [!UICONTROL DIL]. If you don't know your [!DNL Analytics] or [!DNL AppMeasurement] version, check the [!DNL Analytics] call that gets made from the page. Version information shown below:

This customer uses [!DNL Analytics] version 24.4:

```
https://112.2o7.net/b/ss/.../1/H.24.4/...
```

This customer uses [!DNL AppMeasurement] version 3.5.2:

```
https://112.2o7.net/b/ss/.../0/FAS-3.5.2-AS3/...
```

<br>&nbsp;

**Can I collect page data if I'm not a [!DNL Analytics] customer?**

Yes. The [!UICONTROL DIL] module helps you collect page data even if you're not using [!DNL Analytics]. When set up properly, [!UICONTROL DIL] can capture data from and about:

* Meta tags
* URLs and URL headers
* Search engine types
* Keywords

Additionally, clients can deploy a simple onsite object and populate it with key-value pairs that you want [!UICONTROL DIL] to collect data on. This lets you add and remove specific audience data points on your site without any [!DNL Audience Management] updates. Work with your Partner Solutions representative to properly set this up and ensure the [!DNL DIL] module references the page object correctly.

<br>&nbsp;

**Can [!UICONTROL DIL] collect data from [!DNL Google Analytics]?**

Yes. [!UICONTROL DIL] can collect some [!DNL Google Analytics] (GA) elements and pass that data to [!DNL Audience Manager]. See:

* [GA.submitUniversalAnalytics](../dil/dil-modules.md#ga-submit-universal-analytics) 
* [GA.init](../dil/dil-modules.md#ga-init)

<br>&nbsp;

**Can I get raw data from [!DNL Audience Manager] and how granular is it?**

Yes, [!DNL Audience Manager] can provide you with data collected for users we've seen on your inventory. This includes:

* The unique user ID (UUID) assigned by [!DNL Audience Manager]
* Trait and segment IDs
* Unused signals
* Time stamps
* Page URLs

<br>&nbsp;

**I want to collect data on one site and target users via DFP on a different site. Do I need to deploy code on the other property if I don't want to collect data from that location?**

No. If data collection on the second site is not a requirement, you don't need to deploy DIL there. As long as you have access to the inventory on the second site via DFP, you can use the data collection from the initial site and target via DFP.

<br>&nbsp;

**What is the best third-party data provider?**

Each provider brings something unique to the table, so the answer depends on what you're looking for. We can enable overlap reporting (at no cost) to help you understand which provider may work best for you.

<br>&nbsp;

**How does [!DNL Audience Manager] set cookies and pass variables to DFP?**

[!DNL Audience Manager] sets 2 cookies: One sends segment variables to the DFP ad tag and the other sets our unique user ID (UUID), which is also read by DFP. Adding the UUID to the ad tag means we can do user-level reporting and audience discovery.

<br>&nbsp;

**Can we send a DSP information about points in the conversion funnel reached by a user?**

Yes. We can send funnel data, but the DSP must have the technical capability to use it. A DSP must confirm they can handle multiple segments. If they cannot, we may need to create specific segments to pull a user out of other segments based on their conversion progress (e.g., completed step 1 and 2 but not step 3). You may want to send this information to a DSP so they can retarget users, direct them to a specific landing page, or display specific creatives.

<br>&nbsp;

**How can I confirm that data sent via FTP has been picked up by [!DNL Audience Manager]?**

A file has been picked up when the extension changes from `.sync` to `.processed`. When this happens, the file is in the ingestion queue. Also, your account manager can confirm when a file has been uploaded.

<br>&nbsp;

**I want to test the functionality of the [DCS API](../api/dcs-intro/dcs-event-calls/dcs-event-calls.md). I am sending event calls like the one shown below. The calls contain [Declared IDs](../features/declared-ids.md) and signals, which should realize some traits and segments I have already set up. Can I use the [!UICONTROL General Reports] and [!UICONTROL Trend Reports] to verify if the trait and segment populations are increasing?**

```
https://apse2.demdex.net/event?d_rtbd=json&d_cid=123456%01abc123&c_events=placed-an-order
```

No, do not rely on the [!UICONTROL General Reports] and [!UICONTROL Trend Reports] in this case.

The reports compute populations based on the unauthenticated profile records (UUIDs) we see in the backend at the time the reports are generated.

On a first call to the [!UICONTROL DCS], the declared IDs are *not* linked to any UUID (i.e. no [demdex cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_am.html) is present on the client side). The [!UICONTROL DCS] will randomly generate a UUID and set a [!DNL demdex] cookie and pass it on in the response call, but it will not transmit the UUID to the backend.

>[!NOTE]
>
>The generated UUID will only be materialized in our backend data storage once the device on which the cookie is set will trigger further activity.

For this reason, the reports will not reflect the events triggered by the declared IDs in your call. We recommend you use UUID, ECID (formerly MID) or mobile device IDs in event test calls to the [!UICONTROL DCS]. Then, you can verify the trait and segment realizations in the [!UICONTROL General Reports] and in the [!UICONTROL Trend Reports].

See also, the [Index of Audience Manager IDs](../reference/ids-in-aam.md).

<br>&nbsp;

**How long does it take for user profiles to sync across [regions](../api/dcs-intro/dcs-api-reference/dcs-regions.md)?**

It usually takes up to 24 hours for a user profile to sync across regions. However, in rare cases, the process can take up to 48 hours.
