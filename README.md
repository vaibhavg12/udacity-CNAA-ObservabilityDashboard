**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation

![alt monitoring namespace](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/monitoring_svc_pods.png)

![alt observability namespace](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/observability_svc_pods.png)

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.

![alt grafana login page](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/grafana_login_page.png)

![alt grafana home page](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/grafana_home_page.png)

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

![alt basic dashboard with Prometheus as datasource](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/basic_dashboard_with_prometheus_datasource.png)

## Describe SLO/SLI
*TODO:* Describe, in your own words, what the SLIs are, based on an SLO of *monthly uptime* and *request response time*.

SLO
Servlice level objective is a target value (or range of values) for a service level measured over a time unit. Typically, SLO defines the goal for a metric.

SLI
Service level indicator is a quantitative measure of a metric. It a function of X (quantative metric) over Y (time defined by SLO). Typically, SLI tell us how well the service performe for the defined SLO.

monthly uptime: measures availability of a service. For eg: your SLO could be that your systems will be available 99.95% of the time, then your SLI is the actual measurement of your uptime. It could be 99.96% or 99.94% or 99.5%. 

request response time: measures the amount of time a service takes to respond to a client's request. For eg: if your SLO is 2 seconds for a user request and response time for our service and if the service took 1.6 seconds to response a request, then SLI would be 1.6 seconds.


## Creating SLI metrics.
*TODO:* It is important to know why we want to measure certain metrics for our customer. Describe in detail 5 metrics to measure these SLIs. 

1. Latency - it measures the time taken to respond to a request. This is important because customers must know the expected turnaround time for a request.
2. Uptime - it measures percentage of time the service is available and functioning. This tells the customers how much our service will be available for them.
3. Failure Rate - it measures the count of failures over time. This shows how reliable our service is and helps with reputation building.
4. Network Capacity - it measures the average bandwidth in unit time. This indicates how much traffic our network can handle, the more the better.
5. Resource Capacity - it measures the usage of resources i.e. how much RAM and CPU the service is using. This way we can scale them accordingly or increase the memory. if required. 


## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

![alt custom dash](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/custom_dashboard.png)

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name: Vaibhav Gupta

Date: March 13, 2021

Subject: backend service star endpoint says "Method Not Allowed" error 405.

Affected Area: star endpoint (<<host>>/star)

Severity: High

Description: The Mongo database connection cannot be found. The tracer span is 792cfbb2a66c579f.


## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.
**SLOs:**

1. Latency: Application responses should be served within 2000 ms per month. 
2. Uptime: 99% of uptime per month
3. Failure Rate: .05% of 40x/50x responses per month.
4. Network Capacity: the network must be able to serve upto 10Mb data per month
5. Resource Capacity: Monthly average CPU usage should be 65% or less

**SLIs:** 

(All numbers are for month of februaury 2023)
1. Latency Report: average 1150 ms for all requests.
2. Uptime: the average uptime for webservice is around 99.5%.
3. Failure Rate: less than 1% of total requests had 50x response.
4. Network Capacity: average data served by network was around 5.3Mb
5. Resource Capacity: The average CPU usage is around 25.9%

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

1. It took an average of 1070 ms for incoming requests to be served.
   - Monthly traffic - indicates the number of requests served
   - Monthly uptime - indicates the total usability
   - Latency - indicates average response time.
2. the average uptime for webservice is around 98%.
   - Monthly traffic - indicates the number of requests served
   - Monthly uptime - indicates the total usability
   - 20x code reponses - indicates general availability
3. Less than 1% of the total incoming requests had 40x/50x responses
   - Monthly downtime - tells the time period for which serivce was not available
   - Errors per month - tells the failure rate (errors) of application
4. Average data served by network was around 5.3Mb
   - Monthly memory usage of pod used by the application - indicates average memory is used by the source pod of the application.
   - Monthly memory usage of all the pods -  indicates average memory used by all the pods required to run the application.
5. The average CPU usage of the application is 25.9%
   - Monthly memory usage of pod used by the application - indicates average memory is used by the source pod of the application.
   - Monthly memory usage of all the pods -  indicates average memory used by all the pods required to run the application.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  

1. Latency panel - it shows the average response time of the application per request.  this represents the 20x/30x (successful) responses.
2. Uptime panel - shows the availability of application in terms of successful (20x/30x) responses 
3. 40x requests panel - shows a ratio of 40x responses to total responses.
5. 50x requests panel - shows a ratio of 40x responses to total responses.
4. CPU Usage panel - it is an indicator of the avg CPU (memory) usage of the different containers.
5. Network Capacity - shows average data processed by the system