<details>
  <summary> Interact with GCP (Project)</summary>
  
There are 4 ways to interact with Google Cloud
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
## Creat CI with Jenkins

*  Jenkins is an open-source continuous integration environment.
*  Define jobs in Jenkins that can perform tasks such as running a scheduled build of software and backing up data. Notice the software that is installed as part of Jenkins shown in the left side of the description.
*  Marketplace, is part of Google Cloud, Jenkins template is developed and maintained by an ecosystem partner named Bitnami.
```
Marketplace -> Bitnami package for Jenkins
sudo /opt/bitnami/ctlscript.sh restart // to restart jenkins
```
* You had Jenkins UI and that you had administrative access control over Jenkins

## Project

```
gcloud config list //see confis
gcloud config set project projectNameId

```

* QA: There are four ways you can interact with Google Cloud: There’s the Cloud Console, Cloud Shell and the Cloud SDK, the APIs, and the Cloud Mobile App. The Cloud Explorer is not a Google Cloud tool
* QA: The Cloud Console is a graphical user interface and Cloud Shell is a command-line tool. Both tools allow you to interact with Google Cloud. Even though the Cloud Console can do things Cloud Shell can't do and vice-versa, don’t think of them as alternatives, but think of them as one extremely flexible and powerful interface.

</details>

<details>
  <summary> Virtual Network </summary>

GCP uses a software defined network, that is built on a global fiber infrastructure.

* The PoPs, are where Google's network is connected to the rest of the internet. Google Cloud can bring its traffic closer to its peers, because it operates an extensive global network of interconnection points. The network connects regions and PoPs, and is composed of a global network of fiber optic cables with several submarine cable investments.

## Networks

The default quota for each project is 15 networks.
* These networks can be shared with other projects, or they can be peered with networks in other
* These networks do not have IP ranges but are simply a construct of all of the individual IP addresses and services within that network.
* Google Cloud’s networks are global,

### Types of Networks
* `Default`: Every project is provided with a default VPC network with preset subnets and firewall rules. a subnet is allocated for each region with non-overlapping CIDR blocks and firewall rules that allow ingress traffic for ICMP, RDP, and SSH traffic from anywhere, as well as ingress traffic from within the default network for all protocols and ports.
*  `auto mode network`: one subnet from each region is automatically created within it. These automatically created subnets use a set of predefined IP ranges with a /20 mask that can be expanded to /16. All of these subnets fit within the 10.128.0.0/9 CIDR block.
*  `custom mode network` does not automatically create subnets. complete control over its subnets and IP ranges. decide which subnets to create, in regions you choose.
*  custom mode networks cannot be changed to auto mode

### Same Network vs Same Region

* If two VM have same network they can comunicate withing their internal ip ranges even if they are in different regions
* On the other hand, being in same region but different network they need their `external ip` address to comunicate. It is not touching public internet but it needs to go to `Google Edge Router`

### VPC 
* So VPC can globally comunicate internally. So when connect your machine (on premise) to VPC using VPN, then you can use VPC to comunicate withing VMs, this helps to reduce costs and compelexity

### Subnets
* Every subnet has four reserve ip address, first, second and last one. Subnets can be crossed zones in same region. So VM can be on the one subnet but different zones. For example 10.0.0.2 to VM1 at Zone1 and 10.0.0.3 at Zone2 on VM2. Both are in one region. -> Advantage-> Single firewall rule can be used for both VMs.
* Subnet masks should not have overlap with othr subnets in any region in same VPC
* Auto mode subnets ip range are between /20 to /16 but not larger than 16
* Avoid makeing large ip range subnets

### 10.0.0.0/29 how many instance?
* Above can have only 4 instance in subnet, `the 5th one get subnet` exhasted error
* 32-29 = 3 -> 2Power 3 = 8, 4 already reserverd and 4 free
* 10.0.0.0/20 -> 4096 subnets -> physical limitation may exist you can't really use all 4000 of them
* 10.0.0.0/23 -> 512 subnets
* 10.0.0.0/16 = 10.0.0.0 - 10.2.0.0

### Internal Ip Address vs External

* Every VM and every service gets internal IP address like app engines k8
* There is internal DNS service scope to netwrok VM name + ip address, but can't from VM different network
* External Ip is optional. Can be assigned from pool ephemal.
* VM doesn't know external it is map to internal

### DNS Zone 
* Google has DNS zonal and global, but suggested zonal DNS
FQDN is
```
[hostname].[zone].c.[project-id].internal
```
* Cloud DNS translate Domain names into ip addresses
* Map External to internal If you run  `sudo /sbin/ifconfig` you get internal ip address 

### Firewall
* Firewall exist between instances even in the same VPC.
* Firewall rules are stateful. If connection is allowes meaned all trafic in either direction is allowed
* If firewall rules deleted default is deny all ingress and allow all egress trafic
* Fire wall rules includes
* Direction: inbound and outbound (ingress and egress)
* Source: ( source or destination)
* Protocol and ports
* Action: Allow or Deny
* Priority: priority of the rule
* Rule Assignment: Default assign all rules to all instances but we can assign certain rules to certain instances
* GCP pricing calculator https://cloud.google.com/products/calculator
* mynetwork-allow-icmp allows to ping networks internally and externally `ping -c 3 ipaddress` 



</details>













