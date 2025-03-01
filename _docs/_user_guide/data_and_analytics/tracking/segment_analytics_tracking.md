---
nav_title: Segment Analytics Tracking
article_title: Segment Analytics Tracking
page_order: 8
page_type: reference
description: "This reference article covers Segment Analytics tracking and how to view revenue and purchases over time, sessions over time, and custom events over time."
tool: 
  - Segments
  - Reports
---

# Segment analytics tracking

> When you turn on analytics tracking for a segment, you can view sessions, custom events, and revenue over time for this segment.

![Analytics tracking toggle for a segment][16]

If you don't turn analytics tracking on for a segment, you can still access [real-time statistics][11] for that segment and target its users with campaigns. The only difference is the access to the specific analysis tools mentioned on this page.

An app can have tracking turned on for up to 25 segments. Braze recommends tracking segments that are important for you to analyze when understanding your campaigns' effects on sessions, revenue, and purchases.

## Revenue and purchases over time

On the **Revenue** page of the dashboard, you can view data on [revenue and purchases over time for this segment][14].

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), you can find the **Revenue Report** under **Analytics** > **Reports** > **Revenue Report**.
{% endalert %}

To visually compare segment data for any custom time range, add or remove segments from the graph. Select **By Segment** and search for your segments to view them in the chart. Click any legend item to toggle visibility for that metric on or off.

![Revenue data by segment][17]

## Sessions over time

Similarly, you can find data on [sessions over time for this particular segment][13] on the **Overview** page.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), the **Overview** page is now **Home**.
{% endalert %}

![Session data by segment][18]

## Custom events over time

Braze also provides the ability to view data on [Custom events over time for segments][20], via the **Custom Events** page.

{% alert note %}
If you are using our [updated navigation]({{site.baseurl}}/navigation), you can find **Custom Events** under **Data Settings**.
{% endalert %}


[11]: {{site.baseurl}}/user_guide/data_and_analytics/reporting/viewing_and_understanding_segment_data/#segment-statistics
[13]: {{site.baseurl}}/user_guide/data_and_analytics/export_braze_data/exporting_app_usage_data/#exporting-app-usage-data
[14]: {{site.baseurl}}/user_guide/data_and_analytics/export_braze_data/exporting_revenue_data/
[16]: {% image_buster /assets/img_archive/A_Tracking_2.png %}
[17]: {% image_buster /assets/img_archive/Revenue.png %}
[18]: {% image_buster /assets/img_archive/events_over_time2.png %}
[20]: {{site.baseurl}}/user_guide/data_and_analytics/custom_data/custom_events/
