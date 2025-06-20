# Introduction

Sensordata is becoming increasingly important in the Dutch public sector. Smart cities initiatives, citizen
science projects as well as nationwide sensor networks for specific tasks (e.g. environmental monitoring)
have been increasing the amount of sensordata available. Being able to make sense of this data and
combining data from diverse source in applications such as digital twins is increasing the need to standardize
sensordata. 

## Goal of the testbed

We want to explore how standards for sensors can help the public sector better organize and leverage their
available sensordata.
We want to address these questions based upon typical use cases and user questions we have identified.
Geonovum, in line with its mission, is keen to get the answers; and it seeks to involve the market to do so.
The actual questions and issues to be addressed are described in this document, combined into three
research topics.

## Scope

In this testbed we are looking at implementing standards that apply to sensordata such as sensorthings API,
connected systems API. We have two use cases including sensordata that can be used available to help
anwser the questions.

## Outcome

The results of the testbed are intended to contribute to expand and innovate the Dutch public sector Spatial
Data Infrastructure in a direction that takes into account the possibilities in the market today. Based on the
outcome of this testbed we may take steps to make one or more sensor related standards mandatory within
the Dutch public sector, in order to promote interoperability between sensor networks and encourage reuse.
To this end implementations of standards realized within this testbed will be kept online and available for
further experimentations for 6 months after the testbed ends.

## Use cases
This section describes use cases that were employed within the testbed.

### Use case #1: RIVM air quality 

#### Use case #1A

RIVM has the obligation, according to the EU legislation INSPIRE, to deliver the hourly air quality data for
specific depositions. This data is generated out of the AQ database on a hourly basis, harvested with a
python script and saved on the specific SOS inspire webserver. (https://inspire.rivm.nl/sos/eaq/#map)
The SOS software was created by https://52north.org/ as a tool for ArcGIS Server and adapted for the RIVM
to operate on a Apache Tomcat instance as Open Source Software tool (https://github.com/52North/SOS/).
Since the implementation of the software in 2013 this software has never been down except for maintenance.
To be future proof as an organization and to comply to the newer Open Standards available, we as RIVM
would like to investigate the options, possibilities and risks to replace their SOS instance with a OGC
SensorThings API standard, OGC connected systems API or even better an Observations Measurements and
Sampling (OMS) solution.

#### Use case #1B

In an effort to support citizen science in The Netherlands, RIVM also hosts the ‘Samen Meten’ platform: a
data infrastructure that brings together official hourly air quality measurements and sensor-based civil
measurements of local air quality. These sensor data are currently made available to the public through a
STA v1.0 API server (https://api-samenmeten.rivm.nl/v1.0). A brief introduction to this service may be
found at one of the following two webpages:
• English: https://www.samenmeten.nl/international/API
• Dutch: https://www.samenmeten.nl/dataportaal/api-application-programming-interface
We offer this service as an example of how a STA can be used in practice and as a dataset to query or import
as part of this testbed. Further, we would like to investigate how this API service could be improved to
provide better metadata, for instance through an implementation of the STAplus extension (
https://docs.ogc.org/is/22-022r1/22-022r1.html) or an exploration of appropriate metadata standards.

### Use case #2 Municipality of Rotterdam

The municipality of Rotterdam has a multitude of sensors transmitting on LoRa via chirpstack that produce
raw JSON. These sensors measure groundwater levels, soil moisture, soil Ph and temperature, water leakage
and in addition there are people counting sensors and 12-1 weather stations( that measure 12 weather
related parameters). These are documented in more detail (including example JSON) in an attachment
provided with this invitation to tender.
They would like to gain experience in having these sensors exposed through interoperable standards such
as Sensorthings API or connected systems API. 

## Research questions

The research topics, although overlapping in scope, are specifically chosen to address different leading
perspectives and goals. Below these are spelled out, for each of the three research topics.

### Research topic #1: Communicating with a collection of sensors

There are many use cases where one type of sensor is placed in many locations. There is great utility in
querying all of these sensors at the same time with one simple operation. For example "give me all current
temperature readings from the collection of temperature sensors in the municipality of Rotterdam". We want
to know how this can be achieved using different OGC API standards and what the benefits and negatives
for each standard are in practice.


### Research topic #2: Visualisation & analysis

An important aspect of working with sensor data is, of course, being able to get the data and load it into an
application for visualisation and analysis. This research question is about demonstrating that this works,
both in a web viewer and in a dashboard application (e.g. Grafana).

### Research topic #3: Initial device registration

Initial device (aka Thing) registration in a system is not well documented or standardized and hinders
uniformization and encourages bespoke solutions.
‘Things’ are made in the factory by the thousands, all with the same firmware specified by the manufacturer.
The Things have several sensors (possibly different ones) on - board that will measure values. When the
thing is first turned on, it will try to connect to a service (over eg a LoRaWAN Network or the internet over
a 3G network) specified in the firmware.
When this connection is established, the thing must register itself with that service. The thing ‘comes ashore’
for the first time.

## reading guide
The rest of this document contains the results of all three research topics.