### Interact with GCP

* There are 4 ways to interact with Google Cloud
1. Google Cloud Console: it provides a webbased user interface 
2. Cloud Shell CLI: you can use command line also Cloud Shell, which is a browser-based
*  Cloud Shell is a temporary virtual machine with 5 GB of persistent disk storage that has the Google Cloud CLI pre-installed.
4. Rest Based API: Google Cloud client libraries expose APIs for two main purposes: App APIs provide access to services, and they are optimized for supported languages, such as Node.js or Python.
* Admin APIs offer functionality for resource management like for infrastructure
5. Cloud Mobile app: you can start, stop, and SSH into Compute Engine instances and see logs from each instance.
* You can also set up customizable graphs showing key metrics such as CPU usage, network usage, requests per second, and server errors.
* 


* You can use the Cloud Shell to manage projects and resources via command line without having to install the Cloud SDK and other tools on your computer.

#### Cloud shell provides the following:

1. Temporary Compute Engine VM
2. Command-line access to the instance via a browser
3. 5 GB of persistent disk storage ($HOME dir)
4. Pre-installed Cloud SDK and other tools
5. gcloud: for working with Compute Engine and many Google Cloud services
6. gcloud storage: for working with Cloud Storage
7. kubectl: for working with Google Kubernetes Engine and Kubernetes
8. bq: for working with BigQuery
9. Language support for Java, Go, Python, Node.js, PHP, and Ruby
10. Web preview functionality
11. Built-in authorization for access to resources and instances

#### Create Bucket 

```
gcloud storage buckets create gs:\\amirnabaei_bucket_testcase_only
```
* Upload a file into cloud shell using dots and run below
```
gcloud storage cp jobs.pdf  gs://amirnabaei_bucket_testcase_only
gcloud compute regions list //list availbale regions
INFRACLASS_REGION=us-west3 //create global variable
echo $INFRACLASS_REGION
```
#### Append the environment variable to a .profile

* To create a persistent state in Cloud Shell, .profile needs to update
```
mkdir infraclass
touch infraclass/config
echo INFRACLASS_REGION=$INFRACLASS_REGION >> ~/infraclass/config //Append the value of your Region environment variable to the config file:

INFRACLASS_PROJECT_ID=[YOUR_PROJECT_ID]
echo INFRACLASS_PROJECT_ID=$INFRACLASS_PROJECT_ID >> ~/infraclass/config 

source infraclass/config
echo $INFRACLASS_PROJECT_ID

//Edit the shell profile
vi .profile
source infraclass/config
```



















