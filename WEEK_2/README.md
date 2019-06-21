## Modern data pipeline challenges - 01_en

## Message-oriented architectures with Cloud Pub/Sub - 02_en

### IoT devices present new challenges to data ingestion

* Data streaming from varios processes or devices
* Distruting event notifications (ex: new user sign up)
* Scale to handle volume
* Reliabe(no duplicates)

![Cloud Pub/Sub offers reliabe, real-time messaging](../images/CloudPubSub.png)
![Google Cloud Serverless Big Data Pipeline](../images/GoogleCloudServerlessBigDataPipeline.png.png)

## Designing streaming pipelines with Apache Beam - 03_en

* [Apache Beam](https://beam.apache.org/get-started/beam-overview/) is an open source, unified model for defining both batch and streaming data-parallel processing pipelines. Using one of the open source Beam SDKs, you build a program that defines the pipeline. The pipeline is then executed by one of Beam’s supported __distributed processing back-ends__, which include Apache Apex, Apache Flink, Apache Spark, and Google Cloud Dataflow.

![Dataflow Offers NoOps Data Pipelines](../images/DataflowOffersNoOpsDataPipelines.png)

## Implementing streaming pipelines on Cloud Dataflow - 04_en

![Implementation With Google DataFlow](../images/ImplementationWithGoogleDataFlow.png)

![Workflow With Dataflow](../images/WorkflowWithDataflow.png)

* [Dataflow templates](https://cloud.google.com/dataflow/docs/guides/templates/provided-templates)

## Visualizing insights with Data Studio - 05_en

## Creating charts with Data Studio - 06_en

## Demo: Data Studio walkthrough - 07_en

## Lab: Create a Streaming Data Pipeline for a Real-Time Dashboard with Cloud Dataflow

*   Connect to a streaming data Topic in Cloud Pub/sub
*   Ingest streaming data with Cloud Dataflow
*   Load streaming data into BigQuery
*   Analyze and visualize the results

```sh
bq mk taxirides
```

```sh
bq mk \
--time_partitioning_field timestamp \
--schema ride_id:string,point_idx:integer,latitude:float,longitude:float,\
timestamp:timestamp,meter_reading:float,meter_increment:float,ride_status:string,\
passenger_count:integer -t taxirides.realtime
```

## Module Review

### Relational databases are a good choice when you need:

* Streaming, high-throughput writes
* Fast queries on terabytes of data
* Aggregations on unstructured data
* __Transactional updates on relatively small datasets__

### Cloud SQL and Cloud Dataproc offer familiar tools (MySQL and Hadoop/Pig/Hive/Spark). What is the value-add provided by Google Cloud Platform? (Select all of the correct options)

* It’s the same API, but Google implements it better
* Google-proprietary extensions and bug fixes to MySQL, Hadoop, and so on
* Fully-managed versions of the software offer no-ops
* Running it on Google infrastructure offers reliability and cost savings

## Where is unstructured ML used in business? - 08_en

[movemirror](g.co/movemirror)

## How does ML on unstructured data work? - 09_en

## Comparing approaches to ML - 10_en

[cloud.google/vision](cloud.google/vision)
[cloud.google/translate](cloud.google/translate)
[cloud.google/speech](cloud.google/speech)
[cloud.google/video_inteligence](cloud.google/video_inteligence)

## Using pre-built AI to create a chatbot - 11_en

## Customizing Pre-built models with AutoML - 12_en

## Lab: Classify Images with Pre-built ML Models using Cloud Vision API and AutoML

* Setup API key for ML Vision API
* Invoke the pretrained ML Vision API to classify images
* Review label predictions from Vision API
* Train and evaluate custom AutoML Vision image classification model
* Predict with AutoML on new image

API key:
```sh
export API_KEY=AIzaSyA1cdfTSdfUJhLpHApAYX4D5gFzRSFINj4
gsutil acl ch -u AllUsers:R gs://qwiklabs-gcp-bd5684cd966c5239s/*
```

```json
{
  "requests": [
      {
        "image": {
          "source": {
              "gcsImageUri": "gs://qwiklabs-gcp-bd5684cd966c5239s/cirrus.png"
          }
        },
        "features": [
          {
            "type": "LABEL_DETECTION",
            "maxResults": 10
          }
        ]
      }
  ]
}
```

```sh
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json  https://vision.googleapis.com/v1/images:annotate?key=${API_KEY}

{
  "responses": [
    {
      "labelAnnotations": [
        {
          "mid": "/m/01bqvp",
          "description": "Sky",
          "score": 0.9923278,
          "topicality": 0.9923278
        },
        {
          "mid": "/m/01g5v",
          "description": "Blue",
          "score": 0.98593104,
          "topicality": 0.98593104
        },
        {
          "mid": "/m/0csby",
          "description": "Cloud",
          "score": 0.97880876,
          "topicality": 0.97880876
        },
        {
          "mid": "/m/02q7ylj",
          "description": "Daytime",
          "score": 0.9750122,
          "topicality": 0.9750122
        },
        {
          "mid": "/m/01ctsf",
          "description": "Atmosphere",
          "score": 0.9437642,
          "topicality": 0.9437642
        },
        {
          "mid": "/m/03jn2m",
          "description": "Azure",
          "score": 0.8751225,
          "topicality": 0.8751225
        },
        {
          "mid": "/m/02vwbzz",
          "description": "Electric blue",
          "score": 0.85120857,
          "topicality": 0.85120857
        },
        {
          "mid": "/m/0838f",
          "description": "Water",
          "score": 0.8073041,
          "topicality": 0.8073041
        },
        {
          "mid": "/m/026fm63",
          "description": "Calm",
          "score": 0.7785762,
          "topicality": 0.7785762
        },
        {
          "mid": "/g/11k2xz7mr",
          "description": "Meteorological phenomenon",
          "score": 0.7782771,
          "topicality": 0.7782771
        }
      ]
    }
  ]
}
```


```sh
export BUCKET=qwiklabs-gcp-bd5684cd966c5239-vcm
gsutil -m cp -r gs://automl-codelab-clouds/* gs://${BUCKET}

gsutil cp gs://automl-codelab-metadata/data.csv .
sed -i -e "s/placeholder/${BUCKET}/g" ./data.csv
gsutil cp ./data.csv gs://${BUCKET}

```

## Demo: Text classification done three ways - 13_en

[Labs and Demos github](https://github.com/GoogleCloudPlatform/training-data-analyst)

## Module Review

### If you have an image classification task for identifying whether a car is present in a photo or not, which solution should you try first?

* Try a custom model in BQML first
* Try AutoML Vision first
* Try a custom model in TensorFlow first
* __Try the Cloud Vision API first__

[https://cloud.google.com/vision/automl/docs/](https://cloud.google.com/vision/automl/docs/)
[https://cloud.google.com/vision/#resources](https://cloud.google.com/vision/#resources)
[https://www.coursera.org/specializations/machine-learning-tensorflow-gcp](https://www.coursera.org/specializations/machine-learning-tensorflow-gcp)
[https://www.tensorflow.org/tutorials/](https://www.tensorflow.org/tutorials/)
[https://cloud.google.com/automl-tables/docs/quickstart](https://cloud.google.com/automl-tables/docs/quickstart)