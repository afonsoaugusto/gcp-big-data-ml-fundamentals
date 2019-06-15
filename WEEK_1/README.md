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

## Choosing the right approach - 10_en

### Compute

* Compute Engine
* GKE
* App Engine
* Cloud Functions

### Storage

* Cloud Bigtable
* Cloud Storage
* Cloud SQL
* Cloud Spanner
* Cloud Datastore

### Big Data

![Big Data](../images/BigDataServices.png)
![Suite Big Data](../images/SuiteBigDataGCP.png)

## What you can do with Google Cloud Platform - 11_en
## Activity: Explore real customer solution architectures - 12_en

[cloud.google.com/customers](https://cloud.google.com/customers/#/products=Big_Data_Analytics,Machine_Learning)

## Exploring Existing Big Data Solutions - Lab

### Exploring existing solutions

* Navigate to cloud.google.com/customers/
* Filter Products & Solutions for Big Data Analytics.
* Find an interesting customer use case

__Answer the following questions:__

* What were the key challenges to overcome?

* What tools were used in the solution and for what purpose?

* What was the impact?

## Key roles in a data-driven organization - 13_en

![Roles ML Projects](../images/RolesMLProjects.png)


## Module Review

### What are the common big data challenges that you will be building solutions for in this course? (check all that apply)

* __Migrating existing on-premise workloads to the cloud__
* __Analyzing large datasets at scale__
* Building containerized applications for web development
* __Building streaming data pipelines__
* __Applying machine learning to your datasets__

### You have a large enterprise that will likely have many teams using their own Google Cloud Platform projects and resources. What should you be sure to have to help manage and administer these resources? (check all that apply)

* __A defined Organization__
* __Folders for teams and/or products__
* __A defined access control policy with Cloud IAM__
* A Kubernetes or Hadoop cluster for each project

### Which of the following is NOT one of the advantages of Google Cloud security

* __Google Cloud will automatically manage and curate your content and access policies to be safe for the public__
* Google Cloud will secure the physical hardware that is running your applications and infrastructure
* Google Cloud has tools like Cloud IAM that help you administer and set company-wide security policies
* Google Cloud will manage audit logging of access and use of resources in your account

### If you don't have a large dataset of your own but still want to practice writing queries and building pipelines on Google Cloud Platform, what should you do?

* __Practice with the datasets in the Google Cloud Public Datasets program__
* __Find other public datasets online and upload them into BigQuery__
* __Work to create your own dataset and then upload it into BigQuery for analysis__

### As you saw in the demo, Compute Engine nodes on GCP are:

* Expensive to create and teardown
* Pre-installed with all the software packages you might ever need.
* __Allocated on demand, and you pay for the time that they are up.__
* One of ~50 choices in terms of CPU and memory


## How businesses use recommendation systems - 14_en

## Introduction to machine learning - 15_en

* [Large-Scale Deep Learning For Building Intelligent Computer Systems](https://ai.google/research/pubs/pub44921)

* [Large-Scale Deep Learning for Intelligent Computer Systems](https://storage.googleapis.com/pub-tools-public-publication-data/pdf/44921.pdf)

* Recomentation systems require __data__, a __model__, and training/serving __infrastructure__.

## Challenge: ML for recommending housing rentals - 16_en

## Approach: Move from on-premise to Google Cloud Platform - 17_en

* On-primisse
  - Hadoop (BigData)
  - MySQL (RDBMS)

* GCP
  - DataProc
  - Cloud SQL

![Migrate On-Primisse to GCP](../images/MigrateOnPrimisseToGCP.png)

![ChooseYourSolutionAccessPattern](../images/ChooseYourSolutionAccessPattern.png)

![If Your Data Is](../images/Ifyourdatais.png)

## Demo: From zero to an Apache Spark job in 10 minutes or less - 18_en

## Challenge: Utilizing and tuning on-premise clusters - 19_en

![Turn Down Clusters Scheduled](../images/TurnDownClustersScheduled.png)
![Autoscaling Dataproc](../images/AutoscalingDataproc.png)
![Utilize PVMs reduce costs](../images/UtilizePVMsreducecostsforfault-tolerantworkloads.png)

## Move storage off-cluster with Google Cloud Storage - 20_en

![Change workload location](../images/changeworkloadlocation.png)
![Dataproc Advantages](../images/DataprocAdvantages.png)

## Lab - 21_en

![Objectives](../images/Objectives.png)
![Setup](../images/LabSetup.png)
![Recommendations Dataproc](../images/RecommendationsDataproc.png)

## Lab: Recommend products using Cloud SQL and SparkML

* Create Cloud SQL instance
* Create database tables by importing .sql files from Cloud Storage
* Populate the tables by importing .csv files from Cloud Storage
* Allow access to Cloud SQL
* Explore the rentals data using SQL statements from CloudShell

```sql
CREATE DATABASE IF NOT EXISTS recommendation_spark;

USE recommendation_spark;

DROP TABLE IF EXISTS Recommendation;
DROP TABLE IF EXISTS Rating;
DROP TABLE IF EXISTS Accommodation;

CREATE TABLE IF NOT EXISTS Accommodation
(
  id varchar(255),
  title varchar(255),
  location varchar(255),
  price int,
  rooms int,
  rating float,
  type varchar(255),
  PRIMARY KEY (ID)
);

CREATE TABLE  IF NOT EXISTS Rating
(
  userId varchar(255),
  accoId varchar(255),
  rating int,
  PRIMARY KEY(accoId, userId),
  FOREIGN KEY (accoId) 
    REFERENCES Accommodation(id)
);

CREATE TABLE  IF NOT EXISTS Recommendation
(
  userId varchar(255),
  accoId varchar(255),
  prediction float,
  PRIMARY KEY(userId, accoId),
  FOREIGN KEY (accoId) 
    REFERENCES Accommodation(id)
);

SHOW DATABASES;
```

* connect in mysql instance
```sh
gcloud sql connect rentals --user=root --quiet
```

```sh
echo "Creating bucket: gs://$DEVSHELL_PROJECT_ID"
gsutil mb gs://$DEVSHELL_PROJECT_ID

echo "Copying data to our storage from public dataset"
gsutil cp gs://cloud-training/bdml/v2.0/data/accommodation.csv gs://$DEVSHELL_PROJECT_ID
gsutil cp gs://cloud-training/bdml/v2.0/data/rating.csv gs://$DEVSHELL_PROJECT_ID

echo "Show the files in our bucket"
gsutil ls gs://$DEVSHELL_PROJECT_ID

echo "View some sample data"
gsutil cat gs://$DEVSHELL_PROJECT_ID/accommodation.csv
```

### Generating housing recommendations with Machine Learning using Cloud Dataproc

```sh
echo "Authorizing Cloud Dataproc to connect with Cloud SQL"
CLUSTER=rentals
CLOUDSQL=rentals
ZONE=us-central1-a
NWORKERS=2

machines="$CLUSTER-m"
for w in `seq 0 $(($NWORKERS - 1))`; do
   machines="$machines $CLUSTER-w-$w"
done

echo "Machines to authorize: $machines in $ZONE ... finding their IP addresses"
ips=""
for machine in $machines; do
    IP_ADDRESS=$(gcloud compute instances describe $machine --zone=$ZONE --format='value(networkInterfaces.accessConfigs[].natIP)' | sed "s/\[u'//g" | sed "s/'\]//g" )/32
    echo "IP address of $machine is $IP_ADDRESS"
    if [ -z  $ips ]; then
       ips=$IP_ADDRESS
    else
       ips="$ips,$IP_ADDRESS"
    fi
done

echo "Authorizing [$ips] to access cloudsql=$CLOUDSQL"
gcloud sql instances patch $CLOUDSQL --authorized-networks $ips
```

* Public Ip
35.232.128.138

* Instance Connection Name:
qwiklabs-gcp-685bff2a7965b8e0:us-central1:rentals

```python
#!/usr/bin/env python
"""
Copyright Google Inc. 2016
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
"""


import os
import sys
import pickle
import itertools
from math import sqrt
from operator import add
from os.path import join, isfile, dirname
from pyspark import SparkContext, SparkConf, SQLContext
from pyspark.mllib.recommendation import ALS, MatrixFactorizationModel, Rating
from pyspark.sql.types import StructType, StructField, StringType, FloatType

# MAKE EDITS HERE
CLOUDSQL_INSTANCE_IP = '35.232.128.138'   # <---- CHANGE (database server IP)
CLOUDSQL_DB_NAME = 'recommendation_spark' # <--- leave as-is
CLOUDSQL_USER = 'root'  # <--- leave as-is
CLOUDSQL_PWD  = 'XSys3S5GrwK'  # <---- CHANGE

# DO NOT MAKE EDITS BELOW
conf = SparkConf().setAppName("train_model")
sc = SparkContext(conf=conf)
sqlContext = SQLContext(sc)

jdbcDriver = 'com.mysql.jdbc.Driver'
jdbcUrl    = 'jdbc:mysql://%s:3306/%s?user=%s&password=%s' % (CLOUDSQL_INSTANCE_IP, CLOUDSQL_DB_NAME, CLOUDSQL_USER, CLOUDSQL_PWD)

# checkpointing helps prevent stack overflow errors
sc.setCheckpointDir('checkpoint/')

# Read the ratings and accommodations data from Cloud SQL
dfRates = sqlContext.read.format('jdbc').options(driver=jdbcDriver, url=jdbcUrl, dbtable='Rating', useSSL='false').load()
dfAccos = sqlContext.read.format('jdbc').options(driver=jdbcDriver, url=jdbcUrl, dbtable='Accommodation', useSSL='false').load()
print("read ...")

# train the model
model = ALS.train(dfRates.rdd, 20, 20) # you could tune these numbers, but these are reasonable choices
print("trained ...")

# use this model to predict what the user would rate accommodations that she has not rated
allPredictions = None
for USER_ID in range(0, 100):
  dfUserRatings = dfRates.filter(dfRates.userId == USER_ID).rdd.map(lambda r: r.accoId).collect()
  rddPotential  = dfAccos.rdd.filter(lambda x: x[0] not in dfUserRatings)
  pairsPotential = rddPotential.map(lambda x: (USER_ID, x[0]))
  predictions = model.predictAll(pairsPotential).map(lambda p: (str(p[0]), str(p[1]), float(p[2])))
  predictions = predictions.takeOrdered(5, key=lambda x: -x[2]) # top 5
  print("predicted for user={0}".format(USER_ID))
  if (allPredictions == None):
    allPredictions = predictions
  else:
    allPredictions.extend(predictions)

# write them
schema = StructType([StructField("userId", StringType(), True), StructField("accoId", StringType(), True), StructField("prediction", FloatType(), True)])
dfToSave = sqlContext.createDataFrame(allPredictions, schema)
dfToSave.write.jdbc(url=jdbcUrl, table='Recommendation', mode='overwrite')
```

## Module Review

### Complete the following: You should feed your machine learning model your _______ and not your _______. It will learn those for itself!

* if/then statements, data
* rules, data
* __data, rules__

### True or False: Cloud SQL is a big data analytics warehouse

* True
* __False__

### True or False: If you are migrating your Hadoop workload to the cloud, you must first rewrite all your Spark jobs to be compliant with the cloud.

* True
* __False__


### You are thinking about migrating your Hadoop workloads to the cloud and you have a few workloads that are fault-tolerant (they can handle interruptions of individual VMs gracefully). What are some architecture considerations you should explore in the cloud? Choose all that apply


* __Use PVMs or Preemptible Virtual Machines__
* __Migrate your storage from on-cluster HDFS to off-cluster Google Cloud Storage (GCS)__
* __Consider having multiple Cloud Dataproc instances for each priority workload and then turning them down when not in use__

### Google Cloud Storage is a good option for storing data that: (Select the 2 correct options below).

* Is ingested in real-time from sensors and other devices and supports SQL-based queries
* __May be imported from a bucket into a Hadoop cluster for analysis__
* __May be required to be read at some later time (i.e. load a CSV file into BigQuery)__
* Will be accessed frequently and updated constantly with new transactions from a front-end and needs to be stored in a relational database

### Relational databases are a good choice when you need:

* __Transactional updates on relatively small datasets__
* Fast queries on terabytes of data
* Streaming, high-throughput writes
* Aggregations on unstructured data

### Cloud SQL and Cloud Dataproc offer familiar tools (MySQL and Hadoop/Pig/Hive/Spark). What is the value-add provided by Google Cloud Platform? (Select the 2 correct options below )

* __Fully-managed versions of the software offer no-ops__
* __Running it on Google infrastructure offers reliability and cost savings__
* Google-proprietary extensions and bug fixes to MySQL, Hadoop, and so on
* It’s the same API, but Google implements it better

* [Migrating Hadoop to Google Cloud Platform](https://cloud.google.com/solutions/migration/hadoop/hadoop-gcp-migration-overview)
