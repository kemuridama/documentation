---
title: Trace Ingestion and Indexing
kind: documentation
aliases:
 - /tracing/visualization/search/
 - /tracing/trace_search_and_analytics/
 - /tracing/advanced_usage/
---
{{< img src="tracing/live_search_and_analytics/tracing_without_limits_lifecycle-0.png" style="width:100%;" alt="Trace Journey" >}}

<div class="alert alert-warning">
These features are currently in private beta. <a href="https://docs.datadoghq.com/help/">Reach out to support</a> to be added to the beta.
</div>

## Ingestion Controls

{{< img src="tracing/live_search_and_analytics/tracing_without_limits_lifecycle-1.png" style="width:100%;" alt="Trace Journey" >}}

### Overview


### Span Ingestion

{{< img src="tracing/trace_indexing_and_ingestion/DataIngestion.png" style="width:100%;" alt="Data Ingestion" >}}

By default, most or all of your instrumented services will be able to send 100% of their traffic to Datadog.  High-volume services, or services that experience bursts of higher-than-average traffic may pose an exception.

You can see the ingestion rate, as well as requests per second for your services on the above image, available in-app.

EXPLAIN COLUMNS

### Change the Default Ingestion Rate

{{< img src="tracing/trace_indexing_and_ingestion/ChangeIngestRate.gif" style="width:100%;" alt="Change the Data Ingestion Rate" >}}

For any services that you want to send more traffic than the default percentage this can be configured by adding a generated code snippet to your tracer configuration for that service to ensure that percentage of traffic gets sent, from 0 to 100.

### Legacy Setup

Enable [App Analytics][1] on your Integrations.

## Indexing Controls

{{< img src="tracing/live_search_and_analytics/tracing_without_limits_lifecycle-3.png" style="width:100%;" alt="Trace Journey" >}}

### Retention Filters

After spans have been ingested by Datadog, they will be retained for 15 days according to the indexing filters that have been set on your account.  By default, the only retention filter enabled per service will be the [Intelligent Sampling Filter](#datadog-intelligent-sampling-filter), which will retain error traces and proportional traces representing latency distributions.

You can also create any number of additional [tag-based retention filters](#create-your-own-filter) for your services.


{{< img src="tracing/trace_indexing_and_ingestion/SpanIndexing.png" style="width:100%;" alt="Span Indexing" >}}


EXPLAIN COLUMNS


### Datadog Intelligent Sampling Filter

#### Intro to Tail Based Sampling

#### What is retained by default

{{< img src="tracing/live_search_and_analytics/tracing_without_limits_lifecycle-3.png" style="width:100%;" alt="Trace Journey" >}}

ADD CONTENT:
Errors, Error Diversity, All Resources will have associated Traces in the past (any window)
High Latency in different quartile buckets p75, p90, p95
Low throughput
Outliers
Representative traces from latency bands pXX
True Max of time window

### Create your own filter

{{< img src="tracing/trace_indexing_and_ingestion/SpanIndexingFilter.gif" style="width:100%;" alt="Span Indexing" >}}
<Replace with working GIF>

To customize what spans are indexed and retained for 15 days, you can create, modify and disable additional filters based on tags, and set a % of spans matching each filter to be retained. Any span that is retained will have its corresponding trace saved as well and when it is viewed the full trace context will be available.  In order to be searched by tag in [Historical Search and Analytics][2], however, the span containing the relevant tag must have been indexed.



[1]: /tracing/trace_ingestion_and_indexing/app_analytics
[2]: /tracing/trace_search_and_analytics