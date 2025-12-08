---
title: "Blog 2"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---



# Data-driven approach: Optimizing on-demand cost of AWS Elemental MediaLive

By **Krutarth Doshi**, May 8, 2025 | in [Amazon QuickSight](https://aws.amazon.com/blogs/media/category/analytics/amazon-quicksight/), [Analytics](https://aws.amazon.com/blogs/media/category/analytics/), [AWS Elemental MediaLive](https://aws.amazon.com/blogs/media/category/media-services/aws-elemental-medialive/), [Data Science & Analytics for Media](https://aws.amazon.com/blogs/media/category/industries/entertainment/data-science/), [Industries](https://aws.amazon.com/blogs/media/category/industries/), [Media & Entertainment](https://aws.amazon.com/blogs/media/category/industries/entertainment/), [Media Services](https://aws.amazon.com/blogs/media/category/media-services/), [Monetization](https://aws.amazon.com/blogs/media/category/industries/entertainment/monetization/) | [Permalink](https://aws.amazon.com/blogs/media/data-driven-approach-optimizing-on-demand-cost-of-aws-elemental-medialive/)

In the fast-moving world of live video, optimizing cost while keeping quality high is a constant challenge for media companies. Amazon Web Services [(AWS) Elemental MediaLive](https://aws.amazon.com/medialive/), a cloud live video processing service, offers flexible [pricing options](https://aws.amazon.com/medialive/pricing/) to help. Finding the right balance between on-demand and reserved requires careful analysis of usage patterns.

This post walks through a data-driven approach to managing MediaLive [reservations](https://docs.aws.amazon.com/medialive/latest/ug/reservations.html). By leveraging [AWS Cost and Usage Reports (AWS CUR)](https://aws.amazon.com/aws-cost-management/aws-cost-and-usage-reporting/) and [Amazon QuickSight](https://sunnycloudvn.com/kham-pha-aws-amazon-quicksight-khai-thac-tiem-nang-du-lieu-cho-doanh-nghiep/), you can gain insights into MediaLive usage to make informed reservation decisions and reduce cost.

Before the analysis, recap MediaLive pricing options:

1. **On-Demand pricing**: Pay only for resources you use; you pay hourly for [inputs](https://aws.amazon.com/medialive/pricing/#Input_pricing), [outputs](https://aws.amazon.com/medialive/pricing/#Output_pricing), and [add-on features](https://aws.amazon.com/medialive/pricing/#Add-on_features). Maximum flexibility but potentially higher cost for steady usage.  
2. **Reserved pricing**: Commit to MediaLive for 12 months for discounts up to 70 percent vs on-demand. Significant savings for predictable workloads.

The key is finding the right on-demand vs reserved mix based on your usage patterns.

## Prerequisites

You need the following before trying the solution:

* Proper access to [AWS CUR](https://docs.aws.amazon.com/cur/latest/userguide/cur-s3.html), [Amazon Athena](https://aws.amazon.com/athena/), and [QuickSight](https://docs.aws.amazon.com/quicksight/latest/user/athena.html). Follow least-privilege IAM (see [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)) and do your own due diligence.

* Enable AWS CUR if not already. See [Creating Cost and Usage Reports](https://docs.aws.amazon.com/cur/latest/userguide/creating-cur.html).  
  * CUR granularity must be hourly for this solution so usage patterns are accurate for reservation decisions.  
      
* Set up Athena to analyze data in the S3 bucket that stores your CUR. See [Querying Cost and Usage Reports using Amazon Athena](https://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.htmlhttps://docs.aws.amazon.com/cur/latest/userguide/cur-query-athena.html).  
    
* Set up QuickSight to visualize data from your Athena view. See [Setting up for Amazon QuickSight](https://docs.aws.amazon.com/quicksight/latest/user/setting-up.html).

## Solution

### Create an Amazon Athena database for AWS CUR data

If this is your first time using CUR with Athena, create an Athena database and table on CUR data. Choose one of:

* Use [AWS CloudFormation](https://docs.aws.amazon.com/cur/latest/userguide/use-athena-cf.html) (recommended) to integrate CUR with Athena.

Or

* Create the Athena table [manually](https://docs.aws.amazon.com/cur/latest/userguide/cur-ate-manual.html). You must repeat monthly because the table only covers the current CUR path.

### Create an Amazon Athena view from AWS CUR to query insights

An [Athena view](https://docs.aws.amazon.com/athena/latest/ug/views.html) is a logical table that stores a SQL query as a virtual table, always reading the latest data.

1. To create the view `eml_od_usage`, copy the SQL from the [CUR Query Library (MediaLive OnDemand Usage)](https://catalog.workshops.aws/cur-query-library/en-US/queries/media_services#medialive-ondemand-usage-optimization) into the Athena editor.  
2. Replace the `${table_name}` placeholder before running. For example, if your CUR table is `cur_table` in database `cur_db`, replace **${table_name}** with **cur_db.cur_table.**  
3. Prefix the query with:
   ```
   CREATE OR REPLACE VIEW "eml_od_usage" AS
   ```
   then run it.  
   ![][image1]

   *Figure 1: Create an Amazon Athena view.*

This view feeds QuickSight dashboards to visualize MediaLive spend over time.

### Configure Amazon QuickSight to access the Athena view

Next, [create a QuickSight dataset](https://docs.aws.amazon.com/quicksight/latest/user/create-a-data-set-athena.html) using the Athena views.

1. Add the view `eml_od_usage` from Athena views into QuickSight as a dataset.  
   ![][image2]

   *Figure 2: Add an Amazon Athena view to a QuickSight dataset.*

2. Choose query mode **SPICE**. Click **PUBLISH & VISUALIZE** to create a new [QuickSight analysis](https://docs.aws.amazon.com/quicksight/latest/user/creating-an-analysis.html).  
   ![][image3]  
   *Figure 3: Preview a QuickSight dataset before visualizing*

3. After adding the dataset, [add a refresh schedule](https://docs.aws.amazon.com/quicksight/latest/user/refreshing-imported-data.html#schedule-data-refresh) so it receives new CUR data. Daily or weekly refresh is recommended for better visuals.  
   ![][image4]  
   *Figure 4: Add calculated fields to a QuickSight dataset*

### Build visuals for MediaLive reservations

After adding the dataset, add visuals in the analysis. QuickSight analyses let users create interactive visuals and explore data with filtering, calculations, and custom views.

Follow these steps:

1. From the analysis page, add a visual On-Demand spend by Account ID.
   * Left sidebar: click **Add** in Visual types.  
   * Choose **Pie chart**.  
   * In Data, select **eml_od_usage** (Figure 5).  
   * Add fields **line_item_usage_account_id** and **sum_line_item_unblended_cost**.  
   * Change `sum_line_item_unblended_cost` aggregation to **Sum**.  
   *![][image5]*

   *Figure 5: QuickSight pie/table showing On-Demand cost by Account ID and Input Usage Type.*

2. Add On-Demand cost by Account ID and Usage Type.
   * Click **Add**; choose **Table**.  
   * Ensure **eml_od_usage** is selected.  
   * Add fields **line_item_usage_account_id, line_item_usage_type, round_sum_line_item_usage_amount, sum_line_item_unblended_cost**.  
   * Set `round_sum_line_item_usage_amount` and `sum_line_item_unblended_cost` to **Sum**.  
   ![][image6]

   *Figure 6: QuickSight table of recommended reservations by account and usage type.*

3. Add Recommended reservations by Usage Type.
   * Click **Add**; choose **Table**.  
   * Select **eml_od_usage**.  
   * Add **line_item_usage_type, round_sum_line_item_usage_amount, sum_line_item_unblended_cost, Recommended reservation count**.  
   * Set the two numeric cost fields to **Sum**.  
   * Set Recommended reservation count to **Average**.  
   ![][image7]

   *Figure 7: QuickSight chart showing distribution of On-Demand spend.*

4. Add Recommended reservations and On-Demand spend over time.
   * Click **Add**; choose **Line chart**.  
   * Select **eml_od_usage**.  
   * Add fields **line_item_usage_end_date**, **Recommended reservation count**, **sum_line_item_unblended_cost**.  
   * Aggregate `line_item_usage_end_date` by **WEEK**.  
   * Set Recommended reservation count to **Average**; set `sum_line_item_unblended_cost` to **Sum**.  
   ![][image8]

*Figure 8: QuickSight line/table for Recommended reservations vs On-Demand Spend.*

After these steps  
- You have an analysis page like Figure 9, summarizing MediaLive On-Demand spend and showing reservation recommendations by account and usage type.  
- You can [publish as a dashboard](https://docs.aws.amazon.com/quicksight/latest/user/creating-a-dashboard.html) and [share it](https://docs.aws.amazon.com/quicksight/latest/user/sharing-a-dashboard.html) to track MediaLive spend and usage over time.  

![][image9]  
*Figure 9: QuickSight dashboard for MediaLive cost and reservation recommendations*

## Make reservation decisions with data

- Identify accounts with highest On-Demand cost, then review usage patterns. Combine recommended reservation counts with spend trends to choose reservation size.
- When building a business case, consider components with steady On-Demand spend and growth potential. Hourly CUR data shows regularity of usage to time purchases for savings. For uneven loads or short campaigns, keep flexibility to avoid overcommitment.

## Deploy and monitor your reservation strategy

- After finalizing the strategy, purchase reservations via the [AWS Management Console](https://docs.aws.amazon.com/medialive/latest/ug/purchasing-reservations.html) or [API](https://docs.aws.amazon.com/medialive/latest/apireference/offerings-offeringid-purchase.html). To stay optimal, build monitoring with CUR data and QuickSight dashboards to track reservation utilization.
- [Set proactive alerts](https://docs.aws.amazon.com/quicksight/latest/user/subscriber-alerts.html) for underused reservations or spend spikes. Usage patterns change over time; review and adjust regularly to keep MediaLive delivering maximum value and cost efficiency.

## Conclusion

Using AWS CUR plus Amazon QuickSight visualization, you can optimize AWS Elemental MediaLive cost with strategic reservations. This data-driven approach supports informed decisions balancing savings and flexibility for your media workloads.

The key to success is continuous analysis and adjustment. Review CUR data, QuickSight dashboards, and reservation strategy regularly to keep getting maximum value from MediaLive.

Learn more on the AWS Elemental MediaLive pricing page. Contact an [AWS representative](https://pages.awscloud.com/Media-and-Entertainment-Contact-Us.html) for help accelerating your media business.  
**Krutarth Doshi**

**Krutarth Doshi is a Senior Technical Account Manager at AWS with 10+ years of experience. He has supported ISV customers for the past two years, building custom CUR queries and QuickSight visualizations to solve complex technical challenges.**

[image1]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-1.jpg
[image2]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-2.jpg
[image3]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-3.jpg
[image4]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-4.jpg
[image5]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-5.jpg
[image6]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-6.jpg
[image7]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-7.jpg
[image8]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-8.jpg
[image9]: https://d2908q01vomqb2.cloudfront.net/fb644351560d8296fe6da332236b1f8d61b2828a/2025/05/05/ML-Image-9.jpg
