---
description: To create Profile Merge Rules review and complete the steps in each of the procedures described in this section.
seo-description: To create Profile Merge Rules review and complete the steps in each of the procedures described in this section.
seo-title: Getting Started with Profile Merge Rules
solution: Audience Manager
title: Getting Started with Profile Merge Rules
uuid: 7d32c60f-467c-42dd-afa9-437fd7c473c5
---

# Getting Started with Profile Merge Rules {#getting-started-with-profile-merge-rules}

To create [!UICONTROL Profile Merge Rules], review and complete the steps in each of the procedures described in this section.

<!-- merge-rules-start.xml -->

## Create a Cross-Device Data Source {#create-data-source}

To create a cross-device data source, go to **[!UICONTROL Audience Data > Data Sources > Add New]** and complete the steps for each section described here. Administrator permissions are required to create or edit a cross-device data source.

<!-- create-cross-device-datasource.xml -->

>[!TIP]
>
>See [Data Source Settings and Menu Options](../../features/datasources-list-and-settings.md#settings-menu-options) for descriptions of these different controls.

## Data Source Details {#details}

To complete the [!UICONTROL Data Source Details] section:

1. Name the data source.
1. *(Optional)* Describe the data source. A concise description helps you define the role or purpose of the data source.
1. Provide an integration code. An integration code is your own, unique ID for this data source.
1. In the **[!UICONTROL ID Type]** list, select **[!UICONTROL Cross Device]**.
1. In the **[!UICONTROL ID Definition]** list, select an option that defines the data source type. Options include:
    * **[!UICONTROL Person]**: An ID that defines a single person. This ID can be mapped to multiple [!DNL Audience Manager] IDs.
    * **[!UICONTROL Household]**: An ID that defines a group of people. This ID can be mapped to multiple [!DNL Audience Manager] IDs.

## Data Export Controls {#export-controls}

[Data Export Controls](../../features/data-export-controls.md) are optional classification rules you can apply to a data source and destination. They prevent you from sending data to a destination when that action violates a data privacy or use agreement. Skip this section if you do not use [!UICONTROL Data Export Controls].

## Data Source Settings {#settings}

[!UICONTROL Data Source Settings] section provides multiple options, but these 2 are important for creating a cross-device data source:

* **[!UICONTROL Use as Authenticated Profile]**: Selected by default, this setting lets you build a [!UICONTROL Profile Merge Rule] with your own, authenticated data.

* **[!UICONTROL Use as a Device Graph]**: This control is available only to accounts listed as a data provider. Selecting this check box creates your data source as a device graph and lets you share it with other [!DNL Audience Manager] customers. Work with your [!DNL Audience Manager] consultant to get set up as a data provider and to specify which customers this [!UICONTROL Data Source] should be shared with. Your consultant will provision your account and device graph sharing through an internal provisioning processes.

* **[!UICONTROL Data retention for inactive Customer IDs]**: This control allows you to set the data retention period for inactive Customer IDs. This determines how long Audience Manager keeps Customer IDs in our database after they were last seen on the Audience Manager platform. The default value is 24 months (720 days). The minimum value you can set is 1 month and the maximum value is 5 years. Note that we count all months as 30-days. Audience Manager runs a process that deletes inactive Customer IDs once a week, in accordance with the data retention you set for inactive Customer IDs.

The text fields associated with these settings let you rename the [!UICONTROL Data Source] with an alias that appears in the [Profile Merge Rule options](../../features/profile-merge-rules/merge-rule-definitions.md). For example, if you add an alias to **[!UICONTROL Use as Authenticated Profile]**, that name appears in the [!UICONTROL Authenticated Profile Options] list. If you add an alias to **[!UICONTROL Use as a Device Graph]**, that name appears in the [!UICONTROL Device Options] list.

>[!MORE_LIKE_THIS]
>
>* [Create a Data Source](../../features/manage-datasources.md#create-data-source)

## Create a Profile Merge Rule {#create-profile-merge-rule}

To create a [!UICONTROL Profile Merge Rule], go to **[!UICONTROL Audience Data > Profile Merge Rules > Add New Rule]** and complete the steps for each section described here. You can create up to 3 merge rules after setting up a cross-device data source. Administrator permissions are required to create, edit, or delete a rule. All users can view and use existing [!UICONTROL Profile Merge Rules].

<!-- create-profile-merge-rule.xml -->

**Prerequisites:** A cross-device data source is required to build a [!UICONTROL Profile Merge Rule]. See [Create a Data Source](../../features/manage-datasources.md#create-data-source).

>[!TIP]
>
>See [Profile Merge Rule Options Defined](../../features/profile-merge-rules/merge-rule-definitions.md) for descriptions of these different controls.

## Basic Information {#basic-info}

To complete the [!UICONTROL Basic Information] section:

1. Name the [!UICONTROL Profile Merge Rule].
2. *(Optional)* Describe the [!UICONTROL Profile Merge Rule]. A concise description helps you define the role or purpose of your rule.
3. *(Optional)* Select **[!UICONTROL Set as default]** if you want to make this the default [!UICONTROL Profile Merge Rule]. New segments are automatically associated with the default rule.

## Data Export Controls {#data-export-controls}

[Data Export Controls](../../features/data-export-controls.md) are optional classification rules you can apply to your [!UICONTROL Profile Merge Rule]. They prevent you from sending data to a destination when that action violates a data privacy or use agreement. Skip this section if you do not use [!UICONTROL Data Export Controls].

## Profile Merge Rule Setup {#profile-merge-rule-setup}

To complete the [!UICONTROL Proflie Merge Rule Setup] section:

1. Select an **[!UICONTROL Authenticated Option]**. Options include:
    * **[!UICONTROL No Authenticated Profile]**
    * **[!UICONTROL Current Authenticated Profile]**
    * **[!UICONTROL Last Authenticated Profile]**
2. Select an **[!UICONTROL Authenticated Profile Option]** (up to 3, maximum). These are the [cross-device data sources](../../features/profile-merge-rules/merge-rules-start.md) you have created previously.
3. Select a **[!UICONTROL Device Option]**. Options include:
    * **[!UICONTROL No Device Profile]**
    * **[!UICONTROL Current Device Profile]**
    * **[!UICONTROL Profile Link Device Graph]**
    * **[!UICONTROL Device Co-op]**
4. Click **[!UICONTROL Save]**.

## Configure Merge Rule Code {#configure-merge-rule-code}

Follow these instructions to set up the [!UICONTROL Experience Cloud ID Service], [!UICONTROL DIL], and mobile [!DNL SDK] code to work with your merge rules.

<!-- merge-rules-configure-code.xml -->

### Prerequisites

You must set up a [cross-device data source](#create-data-source) and [profile merge rules](#create-profile-merge-rule) *before* completing these procedures.

## For Experience Cloud ID Service Customers {#id-service-customers}

The [!UICONTROL Experience Cloud ID Service] and the latest version of [DIL](../../dil/dil-overview.md) are recommended when working with [!UICONTROL Profile Merge Rules]. However, you don't have to use the [!UICONTROL Experience Cloud ID Service] to work with this feature. If you're just using [!UICONTROL DIL], see the [legacy DIL section](../../features/profile-merge-rules/merge-rules-start.md#legacy-dil) below.

### Configure the Set Customer ID Function

When working with the [!UICONTROL Experience Cloud ID Service], the `setCustomerIDs` function passes declared IDs to [!DNL Audience Manager]. To use a profile merge rule, you must modify `setCustomerIDs` to use the integration code specified when you created a cross-device data source. For example, say you've created a cross-device data source with the integration code `my_datasource_ic`. To pass in a declared ID, you would add the integration code to the visitor ID function as shown in the modified code sample below.

#### Generic code sample

```javascript
visitor.setCustomerIDs({
  "userid":{
      "id":"12345",
      "authState":Visitor.AuthState.AUTHENTICATED
```

#### Modified code sample

```javascript
visitor.setCustomerIDs({
  "my_datasource_ic":{
     "id":"12345",
     "authState":Visitor.AuthState.AUTHENTICATED
```

For more information, see [Create a Cross-Device Data Source](#create-data-source) and [Customer IDs and Authentication States](https://marketing.adobe.com/resources/help/en_US/mcvid/?f=mcvid_customer_ids.html).

### Configure `DIL.create` function

The latest versions of [!UICONTROL DIL] now automatically pick up the [!UICONTROL declared ID] from the `visitorService` function in `DIL.create` (see [Declared ID Variables](../../features/declared-ids.md#declared-id-variables)). Check your `DIL.create` function to make sure this is set up properly as shown in the code sample below.

<pre class="js"><code>
var vDil = DIL.create({
   partner:"partner name",
   visitorService:{
      namespace:"<i>INSERT-MCORG-ID-HERE</i>"
   }
});
</code></pre>

In the namespace key-value pair, the `*`MCORG`*` variable is your [!DNL Experience Cloud] Organization ID. If you don't have this ID, you can find it in the [!UICONTROL Administration] section of the [!DNL Experience Cloud] dashboard. You need administrator permissions to view this dashboard. See [Administration: Core Services](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=admin_getting_started.html).

### Configure SDKs

See the [Configure SDKs](#configure-sdks-legacy-dil) section below.

## Legacy DIL {#legacy-dil}

If you're not using [!DNL Experience Cloud ID Service] yet, you really ought to. But, we understand that moving to new code requires careful thought and testing. In these cases, check your `DIL.create` function to make sure this is set up properly as shown in the code sample below.

<pre class="js"><code>
DIL.create({
   partner:"partner name",
   declaredId:{
      dpuuid:<i>dpuuid</i>,
      dpid:<i>dpid</i>
   }
});
</code></pre>

For more information, see the legacy [!UICONTROL DIL] section in [Declared ID Variables](../../features/declared-ids.md#declared-id-variables).

### Configure SDKs {#configure-sdks-legacy-dil}

Check the methods in your [!DNL SDK] code that let you pass [!UICONTROL declared IDs] from [!DNL Android] and [!DNL iOS] mobile devices. The variable names for the [!DNL Android] and [!DNL iOS] code libraries are the same:

* `dpid`: The cross-device data source ID.
* `dpuuid`: The [!UICONTROL declared ID] (i.e., the user ID).

<table id="table_2ACA3E5F316D4413B10A4403B786CC23"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Device type </th> 
   <th colname="col2" class="entry"> Method </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Android </b> </p> </td> 
   <td colname="col2"> <p> <code> setDpidAndDpuuid </code> </p> <p> <b>Syntax:</b> </p> <p> <pre> public static void setDpidAndDpuuid(String dpid, String dpuuid); </pre> </p> <p> <b>Example:</b> </p> <p> <pre> AudienceManager.setDpidAndDpuuid("myDpid","myDpuuid"); </pre> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> iOS </b> </p> </td> 
   <td colname="col2"> <p> <code> audienceSetDpid:dpuuid </code> </p> <p> <b>Syntax:</b> </p><p>
    <code class="javascript">
      +&nbsp;(void)&nbsp;audienceSetDpid:(NSString&nbsp;*)dpid 
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dpuuid:(NSString&nbsp;*)dpuuid; 
    </code></p>
    <p> <b>Example:</b> </p><p>
    <code class="javascript">
      [ADBMobile&nbsp;audienceSetDpid:@"290"
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dpuuid:@"99301393923940"];
    </code></p>
    </td>
  </tr>
 </tbody>
</table>

See also, [Audience Manager Methods for Android](https://marketing.adobe.com/resources/help/en_US/mobile/android/?f=c_audience_manager_methods.html) and [Audience Manager Methods for iOS](https://marketing.adobe.com/resources/help/en_US/mobile/ios/?f=aam_methods.html).
