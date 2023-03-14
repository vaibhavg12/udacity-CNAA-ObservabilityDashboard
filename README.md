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

![alt tracing in flask app](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/jaeger_span_backend_app.png)

![alt jaeger ui traces](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/jaeger_ui.png)

![alt jaeger ui hompage trace](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/jaeger_ui_homepage_trace.png)

![alt jaeger ui api trace](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/jaeger_ui_api_trace.png)

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

![alt jaeger grafana](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/grafana_source_jaeger_backend.png)

![alt jaeger grafana list](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/grafana_source_jaeger_backend_2.png)

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

![alt tracing in flask app](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/jaeger_ui_star_trace_405.png)

TROUBLE TICKET

Name: Vaibhav Gupta

Date: March 13, 2021

Subject: backend service star endpoint says "Method Not Allowed" error 405.

Affected Area: star endpoint (<<host>>/star)

Severity: High

Description: method not allowed for star api. The tracer span is 955b9083eede0743.

## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.
**SLOs:**

1. Latency: The response time of the 90% requests should be less than 30ms per month. 
2. Uptime: There must be atleast 99% uptime per month.
3. Failure Rate: More than 99% of all requests must execute without any errors.
4. Resource usage: The usage of CPU and RAM must not exceed 80% per month.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

1. Uptime : Given our uptime must be at least 99%, the Uptime KPI helps to measure it.
2. Error Rate : Since more than 99% of all requests must execute without any errors, this KPI helps to see the rate of errors in the application.
3. Resource capcity: This KPI was chosen because the usage of CPU and RAM must not exceed 90% per month. Resource Capacity KPI allows us to monitor their consumption.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  

![alt final dash](https://github.com/vaibhavg12/udacity-CNAA-ObservabilityDashboard/blob/master/answer-img/final_dashboard.png)

1. Memory Utlilization: shows the percentage memory(RAM) used by our applicaiton 
2. CPU Utlilization: shows the percentage CPU used by our applicaiton 
3. Server Uptime: shows the avg uptime of our application 
4. Average Response Time: shows the average latency of our application 
5. Error Responses : shows the ratio of error (40x/50x) HTTP responses to total HTTP responses as a percentage
6. Successful Responses : shows the ratio of successful (20x/30x) HTTP responses to total HTTP responses as a percentage