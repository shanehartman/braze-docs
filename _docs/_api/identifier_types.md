---
nav_title: "API Identifier Types"
article_title: API Identifier Types
page_order: 2.2
description: "This reference article covers the different types of API identifiers that exist in the Braze dashboard, where you can find them, and what they are used for." 
page_type: reference

---

# API identifier types

> This reference guide touches on the different types of API identifiers that can be found within the Braze dashboard, their purpose, where you can find them, and how they are typically used. For information on REST API keys or workspace API keys, refer to the [Rest API key overview]({{site.baseurl}}/api/api_key/)

The following identifiers can be used to access your template, Canvas, campaign, segment, send  or card from Braze's external API. All messages should follow [UTF-8][1] encoding.

{% tabs %}
{% tab App Ids %}

## The app identifier

The app identifier or `app_id` is a parameter associating activity with a specific app in your workspace. It designates which app within the workspace you are interacting with. For example, you will find that you will have an `app_id` for your iOS app, an `app_id` for your Android app, and an `app_id` for your web integration. At Braze, you might find that you have multiple apps for the same platform across the various platform types that Braze supports.

#### Where can I find it?

There are two ways to locate your `app_id`:

1. You can find this `app_id` or application identifier in the **Developer Console** on the **API Settings** tab. On this new page, under **Identification**, you will be able to see every `app_id` that exists for your apps.
2. Go to **Manage Settings**. From this new page, in the **Settings** tab, midway through the page you will find an "API key for **APP NAME** on **PLATFORM**" (e.g "API Key for Ice Cream on iOS). This key is your application identifier.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), these pages are in a new location:<br> - **API Settings** is now **API Keys** and is located at **Settings** > **Setup and Testing** > **API Keys**<br> - **Settings** is now **App Settings** and is located at **Settings** > **Setup and Testing** > **App Settings**
{% endalert %}

#### What can it be used for?

App identifiers at Braze are used when integrating the SDK and are also used to reference a specific app in REST API calls. With the `app_id` you can do many things like pull data for a custom event that occurred for a particular app, retrieve uninstall stats, new user stats, DAU stats, and session start stats for a particular app.

{% alert note %}
Sometimes, you may find you are prompted for an `app_id` but you are not working with an app, because it is a legacy field specific to a specific platform, you can omit this field by including any string of characters as a placeholder for this required parameter.
{% endalert %}

#### Multiple app identifiers

During SDK set up, the most common use case for multiple app identifiers is separating those identifiers for debug and release build variants.
To easily switch between multiple app identifier in your builds, we recommend creating a separate `braze.xml` file for each relevant [build variant][3]. A build variant is a combination of build type and product flavor. Note that by default, a new Android project is configured with `debug` and `release` build types and no product flavors.

For each relevant build variant, create a new `braze.xml` for it in `src/<build variant name>/res/values/`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
<string name="com_braze_api_key">REPLACE_WITH_YOUR_BUILD_VARIANT_API_KEY</string>
</resources>
```
When the build variant is compiled, it will use the new identifier.

{% endtab %}
{% tab Template Ids %}

## Template identifier

A [template]({{site.baseurl}}/api/endpoints/templates/) identifier or template ID is a random key generated by Braze for a given template within the dashboard. Template IDs are unique for each template and can be used to reference templates through the API. 

Templates are great for if your company contracts out your HTML designs for campaigns. Once the templates have been built, you now have a template that is not specific to a campaign but can be applied to a series of campaigns like a newsletter.

#### Where can I find it?
You can find your template ID one of two ways:

1. In the dashboard, open up **Templates & Media** under **Engagement** and select a pre-existing template. If the template you want does not exist yet, create one and save it. At the bottom of the individual template page, you will be able to find your template identifier.<br><br>
2. Braze offers an **Additional API Identifiers** search, Here, you can quickly look up specific identifiers. It can be found at the bottom of the **API Settings** tab within the **Developer Console** page.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), these pages are in a new location:<br>- **Templates & Media** is now **Templates**<br> - **API Settings** is now **API Keys** and is located at **Settings** > **Setup and Testing** > **API Keys**
{% endalert %}

#### What can it be used for?

- Update templates over API
- Grab information on a specific template

<br>
{% endtab %}
{% tab Canvas IDs %}

## Canvas identifier

A [Canvas]({{site.baseurl}}/user_guide/engagement_tools/canvas/) identifier or Canvas ID is random key generated by Braze for a given Canvas within the dashboard. Canvas IDs are unique to each Canvas and can be used to reference Canvases through the API. 

Note that if you have a Canvas that has variants, there exists an overall Canvas ID as well as individual variant Canvas IDs nested under the main Canvas. 

#### Where can I find it?
You can find your Canvas ID in the dashboard. Open up **Canvas** under **Engagement** and select a pre-existing Canvas. If the Canvas you want does not exist yet, create one and save it. At the bottom of an individual Canvas page, click **Analyze Variants**. A window appears with the Canvas API identifier located at the bottom.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), **Canvas** is now located under **Messaging**.
{% endalert %}

#### What can it be used for?
- Track analytics on a specific message
- Grab high-level aggregate stats on Canvas performance
- Grab details on a specific Canvas
- With Currents to bring in user-level data for a "bigger picture" approach to canvases
- With API trigger delivery in order to collect statistics for transactional messages

<br>
{% endtab %}
{% tab Campaign IDs %}

## Campaign identifier

A [campaign]({{site.baseurl}}/user_guide/engagement_tools/campaigns/) identifier or campaign ID is random key generated by Braze for a given campaign within the dashboard. Campaign IDs are unique to each campaign and can be used to reference campaigns through the API. 

Note that if you have a campaign that has variants, there is both an overall campaign ID as well as individual variant campaign IDs nested under the main campaign. 

#### Where can I find it?
You can find your campaign ID one of two ways:

1. In the dashboard, open up **Campaigns** under **Engagement** and select a pre-existing campaign. If the campaign you want does not exist yet, create one and save it. At the bottom of the individual campaign page, you will be able to find your **Campaign API Identifier**.<br><br>
2. Braze offers an **Additional API Identifiers** search, Here, you can quickly look up specific identifiers. You can find this at the bottom of the **API Settings** tab in the **Developer Console**.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), these pages are in a new location:<br> - **Campaigns** is under **Messaging**<br> - **API Settings** is now **API Keys** and is located at **Settings** > **Setup and Testing** > **API Keys**
{% endalert %}

#### What can it be used for?
- Track analytics on a specific message
- Grab high-level aggregate stats on campaign performance
- Grab details on a specific campaign
- With Currents to bring in user-level data for a "bigger picture" approach to campaigns
- With API-triggered delivery in order to collect statistics for transactional messages
- To [search for a specific campaign]({{site.baseurl}}/user_guide/engagement_tools/campaigns/managing_campaigns/search_campaigns/#search-syntax) on the **Campaigns** page using the filter `api_id:YOUR_API_ID`

<br>
{% endtab %}
{% tab Segment IDs %}

## Segment identifier

A [segment]({{site.baseurl}}/user_guide/engagement_tools/segments/) identifier or segment ID is random key generated by Braze for a given segment within the dashboard. Segment IDs are unique to each segment and can be used to reference segments through the API. 

#### Where can I find it?
You can find your segment ID one of two ways:

1. In the dashboard, open up **Segments** under **Engagement** and select a pre-existing segment. If the segment you want does not exist yet, create one and save it. At the bottom of the individual segment page, you will be able to find your segment identifier. <br><br>
2. Braze offers an **Additional API Identifiers** search, Here, you can quickly look up specific identifiers. It can be found at the bottom of the **API Settings** tab within the **Developer Console** page.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), these pages are in a new location:<br> - **Segments** is under **Audience**<br> - **API Settings** is now **API Keys** and is located at **Settings** > **Setup and Testing** > **API Keys**
{% endalert %}

#### What can it be used for?
- Get details on a specific segment
- Retrieve analytics of a specific segment
- Pull how many times a custom event was recorded for a particular segment
- Specify and send a campaign to a members of a segment from within the API

{% endtab %}
{% tab Card IDs %}

## Card identifier

A card identifier or card ID is random key generated by Braze for a given News Feed card within the dashboard. Card IDs are unique to each [News Feed]({{site.baseurl}}/user_guide/engagement_tools/news_feed/) card and can be used to reference cards through the API. 

{% alert note %}
News Feed is being deprecated. Braze recommends that customers who use our News Feed tool move over to our Content Cards messaging channel—it's more flexible, customizable, and reliable. Check out the [migration guide]({{site.baseurl}}/user_guide/message_building_by_channel/content_cards/migrating_from_news_feed/) for more.
{% endalert %}

#### Where can I find it?
You can find your card ID one of two ways:

1. In the dashboard, open up **News Feed** under **Engagement** and select a pre-existing News Feed. If the News Feed you want does not exist yet, create one and save it. At the bottom of the individual News Feed page, you will be able to find your unique card identifier. <br><br>
2. Braze offers an **Additional API Identifiers** search, Here, you can quickly look up specific identifiers. It can be found at the bottom of the **API Settings** tab within the **Developer Console** page.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), these pages are in a new location:<br> - **News Feed** is under **Messaging**<br> - **API Settings** is now **API Keys** and is located at **Settings** > **Setup and Testing** > **API Keys**
{% endalert %}

#### What can it be used for?
- Retrieve relevant information on a card
- Track events related to Content Cards and engagement

<br>
{% endtab %}
{% tab Send IDs %}

## Send identifier

A send identifier or send ID is a key either generated by Braze or created by you for a given message send under which the analytics should be tracked. The send identifier allows you to pull back analytics for a specific instance of a campaign send via the [`/sends/data_series` endpoint]({{site.baseurl}}/api/endpoints/export/campaigns/get_send_analytics/).

#### Where can I find it?

API and API triggered campaigns that are sent as a broadcast will automatically generate a send identifier if a send identifier is not provided. If you want to specify your own send identifier, you will have to first create one via the [`/sends/id/create` endpoint]({{site.baseurl}}/api/endpoints/messaging/send_messages/post_create_send_ids/). The identifier must be all ASCII characters and at most 64 characters long. You can reuse a send identifier across multiple sends of the same campaign if you want to group analytics of those sends together.

#### What can it be used for?
Send and track message performance programmatically, without campaign creation for each send.

<br>
{% endtab %}
{% endtabs %}

[1]: https://en.wikipedia.org/wiki/UTF-8
[3]: https://developer.android.com/studio/build/build-variants.html
