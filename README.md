**Note:** For the screenshots, you can store all of your answer images in the `answer-img` directory.

## Verify the monitoring installation

*TODO:* run `kubectl` command to show the running pods and services for all components. Take a screenshot of the output and include it here to verify the installation

## Setup the Jaeger and Prometheus source
*TODO:* Expose Grafana to the internet and then setup Prometheus as a data source. Provide a screenshot of the home page after logging into Grafana.

## Create a Basic Dashboard
*TODO:* Create a dashboard in Grafana that shows Prometheus as a source. Take a screenshot and include it here.

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

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name:

Date:

Subject:

Affected Area:

Severity:

Description:


## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  
