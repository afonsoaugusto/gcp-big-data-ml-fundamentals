# Introduction to Google Cloud Platform - 02_en

* GCP Infrastructure
    - Compute
    - Storage
    - Networking
    - Security

* Big Data and ML products
    - Google inovation timeline
    - Choosing the right approach

* What you can do with GCP
* Activity: Explore a customer use case
* The different data roles in an organizaton

![GPC Organization](../images/GCP_organization.png)

## Compute Power for Analytic and ML Workloads - 03_en

![Google trains on its infrastructure and deploys to phone hardware](../images/Google_trains.png)

![AI building blocks](../images/AI_building_blocks.png)

## Demo: Creating a VM on Compute Engine - 04_en

[earthquakevm](https://github.com/GoogleCloudPlatform/training-data-analyst/blob/master/courses/bdml_fundamentals/demos/earthquakevm/README.md)

## Elastic Storage with Google Cloud Storage - 05_en

![Types region storage](../images/type_region_storage.png)

![GCP resource hierarchy](../images/GCP_resource_hierarchy.png)

![Gsutil Copy](../images/gsutil_copy.png)

## Build on Google's Global Network - 06_en

## Security: On-premise vs Cloud-native - 07_en

![Cloud Security GCP](../images/Cloud_Security_GCP.png)

## Evolution of Google Cloud Big Data Tools - 08_en

![Google new data processing methods](../images/Google_new_data_processing_methods.png)

![GCP innovation infra](../images/GCP_innovation_infra.png)


# Lab: Explore a BigQuery Public Dataset

## Google Cloud Public Datasets program

* [public_datasets_one_pager](https://services.google.com/fh/files/misc/public_datasets_one_pager.pdf)
* [BigQuery use cases](https://cloud.google.com/bigquery/#bigquery-solutions-and-use-cases)
* [Google Cloud customers who use Big Data tools](https://cloud.google.com/customers/#/products=Big_Data_Analytics)
* [Google Cloud Public Datasets](https://cloud.google.com/public-datasets/)

## Getting Started with Google Cloud Platform and Qwiklabs - 09_en


## Lab:

```sql
SELECT
  name, gender,
  SUM(number) AS total
FROM
  `bigquery-public-data.usa_names.usa_1910_2013`
GROUP BY
  name, gender
ORDER BY
  total DESC
LIMIT
  10
```