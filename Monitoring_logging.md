

### Google Cloud operations suite
* Google Cloud operations is a suite of products to monitor, diagnose and troubleshoot infrastructure, services, and applications at scale. It incorporates capabilities to let DevOps 
users operate services in a manner similar to how Google SREs operate their own services.echnology
* `Cloud Logging` collects and stores all of your application logs, so you can see what's happening under the hood
* `Cloud Monitoring` collects metrics and traces, so you can track the performance of your applications and identify bottlenecks.
* `APM` provides a unified view of your application's performance, so you can quickly identify and fix problems.

* `Monitoring` is defined as collecting, processing, aggregating, and displaying real-time quantitative data about a system, such as query counts and types, error counts and types, processing times,
and server lifetimes
* `incident` can also be used to describe a breach of security.

### A system’s performance and reliability.
* There are 4 golden rules to measure system performance and reliability, they are latency, traffic, saturation, and errors.
* `Latency` measures how long it takes a particular part of a system to return a result. Changes in latency could indicate emerging issues.
* `How larency measured` Sample latency metrics include page load latency, number of requests waiting for a thread, query duration, service response time,
transaction duration, time to first response, time to complete data return.
* `traffic`, which measures how many requests are reaching your system. It’s a core measure when calculating infrastructure spend. Sample traffic metrics include number of HTTP requests per second,
number of requests for static vs. dynamic content, number of Network I/Os, number of concurrent sessions number of transactions per second, number of retrievals per second, number of active requests,
number of write iops, number of read iops and number active connections.
* `Saturation` tells how full the service is. Sample capacity metrics include, percentage of memory utilization, percentage of thread pool utilization,
  percentage of cache utilization, percentage of disk utilization, percentage of CPU utilization, Disk quota, Memory quota, number of available connections and number of users on the system.
* `Errors`  are often raised when a flaw, failure, or fault in a computer program or system causes it to produce incorrect or unexpected results, or behave in unintended ways.
Sample error metrics include wrong answers or incorrect content, number of 400/500 HTTP codes, number of failed requests, number of exceptions, number of stack traces, servers that fail liveness checks and number of dropped connections.


### Monitoring
* Monitoring is the foundation of product reliability.
* Cloud Monitoring provides visibility into the performance, uptime, and overall health of cloud-powered applications. It collects metrics, events, and metadata from projects, logs, services, systems, agents, custom code, and various common application components,
  including Cassandra, Nginx, Apache Web Server, Elasticsearch, and many others. Monitoring ingests that data and generates insights via dashboards, Metrics Explorer charts, and automated alerts.
* Open source standards: Leverage Prometheus and Open Telemetry to collect metrics across compute workloads.

* Automated `logging` is integrated into Google Cloud products like App Engine, Cloud Run, Compute Engine VMs running the logging agent, and GKE.
* You can aggregate and centralize logs at a organizational level, project level and folder level based on your needs.
*  Export log data as files to Google Cloud Storage, or as messages through Pub/Sub, or into BigQuery tables Pub/Sub messages can be analyzed in near-real time
  using custom code or stream processing technologies like Dataflow.
* `Logs-based metrics` may be created and integrated into Cloud Monitoring dashboards, alerts, and service SLOs.
* Admin logs are stored by default for 400 days. Data access logs are retained by default for 30 days, but this is configurable up to a max of 3650 days
* SecOps are in charge of ensuring that all access is authorized and that bad actors are not navigating your network.

### Monitoring Architecture



### Error Reporting

* `Error Reporting` is always watching your service and instantly alerts you when a new application error cannot be grouped with existing ones.
* also helps to directly jump from a notification to the details of the new error.
* You can also create alerts to receive notifications on new errors.

* `Cloud Trace` is a tracing system that collects latency data from your distributed applications and displays it in the Google Cloud console.
* Performance insights are provided in near-real time, and Trace automatically analyzes all of your application's traces to generate in-depth latency reports to surface performance degradations.
* Users have reported that an application occasionally returns garbage data instead of the intended results, but you have been unable to reproduce this problem in your test environment. Which tool might be of best help? Error Reporting
* You want a simple way to see the latency of requests for a web application you deployed to Cloud Run. What Google Cloud tool should you use? Trace
* You want to calculate the uptime of a service and receive alerts if the uptime value falls below a certain threshold. Which tool will help you with this requirement? Cloud Monitoring
* 






  
