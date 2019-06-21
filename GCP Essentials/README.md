## [A Tour of Qwiklabs and the Google Cloud Platform](https://google.qwiklabs.com/focuses/2794?parent=catalog)

## [Creating a Virtual Machine](https://google.qwiklabs.com/focuses/3563?parent=catalog)

* [Create a Virtual Machine, GCP Essentials](https://www.youtube.com/watch?v=ew-r46FmzSM&feature=youtu.be)

```sh
gcloud auth list

          Credentialed Accounts
ACTIVE  ACCOUNT
*       google3853227_student@qwiklabs.net

To set the active account, run:
    $ gcloud config set account `ACCOUNT`

To take a quick anonymous survey, run:
  $ gcloud alpha survey

```

```sh
gcloud config list project

[core]
project = qwiklabs-gcp-f728b2047bca0e0e

Your active configuration is: [cloudshell-16343]
```

* [regions zones](https://cloud.google.com/compute/docs/regions-zones/)

```sh
sudo su -
apt-get update
apt-get install nginx -y
ps auwx | grep nginx
```

```sh
gcloud compute instances create gcelab2 --machine-type n1-standard-2 --zone us-central1-c

Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-f728b2047bca0e0e/zones/us-central1-c/instances/gcelab2].
NAME     ZONE           MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP   STATUS
gcelab2  us-central1-c  n1-standard-2               10.128.0.3   35.239.46.34  RUNNING
```

```sh
gcloud compute ssh gcelab2 --zone us-central1-c
```

## [Compute Engine: Qwik Start - Windows](https://google.qwiklabs.com/focuses/560?parent=catalog)

## [Getting Started with Cloud Shell & gcloud](https://google.qwiklabs.com/focuses/563?parent=catalog)

```sh
gcloud -h

Usage: gcloud [optional flags] <group | command>
  group may be           access-context-manager | ai-platform | alpha | app |
                         asset | auth | beta | bigtable | builds | components |
                         composer | compute | config | container | dataflow |
                         dataproc | datastore | debug | deployment-manager |
                         dns | domains | endpoints | filestore | firebase |
                         functions | iam | iot | kms | logging | ml |
                         ml-engine | organizations | projects | pubsub | redis |
                         resource-manager | scheduler | services | source |
                         spanner | sql | tasks | topic
  command may be         docker | feedback | help | info | init | version

For detailed information on this command and its flags, run:
  gcloud --help
```

```sh
cd $HOME
vi ./.bashrc
```

```sh
gcloud config list

[component_manager]
disable_update_check = True
[compute]
gce_metadata_read_timeout_sec = 5
[core]
account = google3854759_student@qwiklabs.net
disable_usage_reporting = False
project = qwiklabs-gcp-fabd27a3b80a2f0c
[metrics]
environment = devshell

Your active configuration is: [cloudshell-9052]


To take a quick anonymous survey, run:
  $ gcloud alpha survey


gcloud config list --all
[accessibility]
screen_reader (unset)
[app]
cloud_build_timeout (unset)
promote_by_default (unset)
stop_previous_version (unset)
use_runtime_builders (unset)
[auth]
disable_credentials (unset)
[billing]
quota_project (unset)
[builds]
kaniko_cache_ttl (unset)
timeout (unset)
use_kaniko (unset)
[component_manager]
additional_repositories (unset)
disable_update_check = True
[composer]
location (unset)
[compute]
gce_metadata_read_timeout_sec = 5
region (unset)
use_new_list_usable_subnets_api (unset)
zone (unset)
[container]
build_timeout (unset)
cluster (unset)
use_application_default_credentials (unset)
use_client_certificate (unset)
[core]
account = google3854759_student@qwiklabs.net
custom_ca_certs_file (unset)
default_regional_backend_service (unset)
disable_color (unset)
disable_file_logging (unset)
disable_prompts (unset)
disable_usage_reporting = False
log_http (unset)
max_log_days (unset)
pass_credentials_to_gsutil (unset)
project = qwiklabs-gcp-fabd27a3b80a2f0c
show_structured_logs (unset)
trace_token (unset)
user_output_enabled (unset)
verbosity (unset)
[datafusion]
location (unset)
[dataproc]
region (unset)
[deployment_manager]
glob_imports (unset)
[filestore]
location (unset)
zone (unset)
[functions]
region (unset)
[game_services]
location (unset)
[gcloudignore]
enabled (unset)
[healthcare]
dataset (unset)
location (unset)
[interactive]
bottom_bindings_line (unset)
bottom_status_line (unset)
completion_menu_lines (unset)
context (unset)
fixed_prompt_position (unset)
help_lines (unset)
hidden (unset)
justify_bottom_lines (unset)
manpage_generator (unset)
multi_column_completion_menu (unset)
prompt (unset)
show_help (unset)
suggest (unset)
[metrics]
environment = devshell
[ml_engine]
local_python (unset)
polling_interval (unset)
[proxy]
address (unset)
password (unset)
port (unset)
rdns (unset)
type (unset)
username (unset)
[redis]
region (unset)
[spanner]
instance (unset)
[survey]
disable_prompts (unset)

Your active configuration is: [cloudshell-9052]
```

```sh
#Managing Cloud Storage data
gsutil mb gs://unique-name-qwiklabs-gcp-fabd27a3b80a2f0c

vi test.dat
Welcome to gcloud!
gsutil cp test.dat gs://qwiklabs-gcp-fabd27a3b80a2f0c
```

## Kubernetes Engine: Qwik Start

### Kubernetes on Google Cloud Platform

* Load-balancing for Compute Engine instances.
* Node Pools to designate subsets of nodes within a cluster for additional flexibility.
* Automatic scaling of your cluster's node instance count.
* Automatic upgrades for your cluster's node software.
* Node auto-repair to maintain node health and availability.
* Logging and Monitoring with Stackdriver for visibility into your cluster.

```sh
gcloud auth list
gcloud config list project
```

```sh
gcloud config set compute/zone us-central1-a
gcloud container clusters create cluster-central1

kubeconfig entry generated for cluster-central1.
NAME              LOCATION       MASTER_VERSION  MASTER_IP       MACHINE_TYPE   NODE_VERSION  NUM_NODES  STATUS
cluster-central1  us-central1-a  1.12.8-gke.6    35.226.103.253  n1-standard-1  1.12.8-gke.6  3          RUNNING
```

```sh
gcloud container clusters get-credentials cluster-central1
kubectl run hello-server --image=gcr.io/google-samples/hello-app:1.0 --port 8080
kubectl expose deployment hello-server --type="LoadBalancer"
kubectl get service hello-server
http://[EXTERNAL-IP]:8080
gcloud container clusters delete cluster-central1
```

## Set Up Network and HTTP Load Balancers

```sh
gcloud auth list
gcloud config list project
```

```sh
gcloud config set compute/zone us-central1-a
gcloud config set compute/region us-central1
```

```sh
cat << EOF > startup.sh
#! /bin/bash
apt-get update
apt-get install -y nginx
service nginx start
sed -i -- 's/nginx/Google Cloud Platform - '"\$HOSTNAME"'/' /var/www/html/index.nginx-debian.html
EOF

gcloud compute instance-templates create nginx-template \
         --metadata-from-file startup-script=startup.sh

#NAME            MACHINE_TYPE   PREEMPTIBLE  CREATION_TIMESTAMP
#nginx-template  n1-standard-1               2019-06-21T05:56:24.987-07:00

gcloud compute target-pools create nginx-pool

#Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-c27d06d45ab622a8/regions/us-central1/targetPools/nginx-pool].
#NAME        REGION       SESSION_AFFINITY  BACKUP  HEALTH_CHECKS
#nginx-pool  us-central1  NONE

gcloud compute instance-groups managed create nginx-group \
         --base-instance-name nginx \
         --size 2 \
         --template nginx-template \
         --target-pool nginx-pool

#Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-c27d06d45ab622a8/zones/us-central1-a/instanceGroupManagers/nginx-group].
#NAME         LOCATION       SCOPE  BASE_INSTANCE_NAME  SIZE  TARGET_SIZE  INSTANCE_TEMPLATE  AUTOSCALED
#nginx-group  us-central1-a  zone   nginx               0     2            nginx-template     no

gcloud compute instances list

#NAME        ZONE           MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP    STATUS
#nginx-30rd  us-central1-a  n1-standard-1               10.128.0.3   35.232.7.88    STAGING
#nginx-47ts  us-central1-a  n1-standard-1               10.128.0.2   34.66.202.203  RUNNING

gcloud compute firewall-rules create www-firewall --allow tcp:80
```

```sh
gcloud compute forwarding-rules create nginx-lb \
         --region us-central1 \
         --ports=80 \
         --target-pool nginx-pool

gcloud compute forwarding-rules list

#NAME      REGION       IP_ADDRESS    IP_PROTOCOL  TARGET
#nginx-lb  us-central1  34.67.225.82  TCP          us-central1/targetPools/nginx-pool

gcloud compute http-health-checks create http-basic-check

#Created [https://www.googleapis.com/compute/v1/projects/qwiklabs-gcp-c27d06d45ab622a8/global/httpHealthChecks/http-basic-check].
#NAME              HOST  PORT  REQUEST_PATH
#http-basic-check        80    /

gcloud compute backend-services create nginx-backend \
      --protocol HTTP --http-health-checks http-basic-check --global

gcloud compute backend-services add-backend nginx-backend \
    --instance-group nginx-group \
    --instance-group-zone us-central1-a \
    --global

gcloud compute url-maps create web-map \
    --default-service nginx-backend

gcloud compute target-http-proxies create http-lb-proxy \
    --url-map web-map

gcloud compute forwarding-rules create http-content-rule \
        --global \
        --target-http-proxy http-lb-proxy \
        --ports 80

gcloud compute forwarding-rules list
```
