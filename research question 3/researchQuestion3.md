## Research question 3: Device Registration

### State of Research

Device registration, and following that, device management, is an ongoing research topic.
Not just in the context of the Internet of Things, but everywhere where sensors are deployed and managed.
The complexity stems from the fact that there are very many different sensors and sensor types, used in very many different use cases, feeding their data into very many different sensor data management systems over many different communication protocols.
The manufacturer of a Sensor system can’t know in advance the use cases the sensor will be used for, or the sensor data management systems it will need to feed data to.

When deploying a new sensor for a given use case, communicating over an existing communication infrastructure, sending data to an existing sensor data management system, information from four different sources needs to be combined:

- The sensor hardware, such as:
  - Sensor identification
  - Measured parameters
- Communication Infrastructure, such as:
  - Authentication and Authorisation
  - Addresses of brokers or gateways
- Sensor data management system, such as:
  - Authentication and Authorisation
  - API endpoints
- Use case, such as:
  - Feature the sensor observes
  - Location of the sensor
  - Responsible party

The initial configuration of sensor devices is manufacturer specific and needs to be done directly on the device
For instance, many manufacturers of LoRaWAN sensor devices provide a smartphone app that uses Near-Field-Communication (NFC) to directly change the configuration of their devices.
Next to the initial configuration of the device itself, the device also has to be registered on the communication network.
On the case of LoRa, this is often the global network “The Things Network”, but many organisations have their own local LoRa instance using the “Chirpstack” software implementation.
Once the initial configuration is completed, and the device is connected to a LoRa network, the configuration of many devices can also be changed using Over-The-Air updates.

The sensor also has to be registered in the sensor data management system of the organisation that deploys the sensor, so that the data from the sensor can be used for the purpose it was deployed for.
There are many different systems for this, many custom-built for their use case, some based on standards such as O&M, OMS or the SensorThings API.

Because of the enormous diversity in each of the layers involved, the concept of connectors is used to transfer data between the communication infrastructure and the information management system.
A Connector is a piece of software with Extract, Transform, Load (ETL) functionality, that takes data from a source system, transforms the data into the format of the target system, and then loads the data into the target system.
A common piece of software used for this purpose is [NodeRed](https://nodered.org/), that features a browser-based, drag-and-drop interface for creating ETL flows.

One problem with this architecture is directly clear from figure 1: The data from a single sensor has to be managed and kept synchronised over multiple systems.
![Generic IoI Architecture with many different Admin interfaces](Generic-IoT-Architecture.drawio.png)


Taking a typical LoRa device, using NodeRed as ETL stack, the process looks something like this:

1. **Device**: Configure the device by setting the identifiers and secrets used to join the LoRa network and configure the intervals in which measurements are made.
1. **LoRa Network**: Register the device
   1. Create a device object in the LoRa network stack with the identifiers and secrets from the previous step.
   1. Set up a low-level decoder to decode the payload of the sensor into a generic JSON object.
      If multiple devices of the same type are used, this generally only needs to be done once.
1. **SensorThings Service**: Create entities for managing the sensor data
   1. Create a Thing with a Location
   1. For each Sensor on the device, create an ObservedProperty instance if a suitable one is not already present.
   1. For each Sensor on the device, create a Sensor instance if a suitable one is not already present.
   1. For each Sensor on the device, create a Datastream, linked to the Thing, a Sensor and an ObservedProperty.
1. **NodeRed**: Create the workflow that can decode the generic JSON object and insert each value into the correct Datastream for the device.


Device Registration is also only the first step in the long process of device management.
Devices can break, be moved around, and be decommissioned.
Battery lifetime needs to be tracked to ensure they are exchanged in time and sensors need to be monitored to ensure they still work as expected.
It is quite likely that the admin in the diagram will start using a spreadsheet to keep track of his sensors, thus adding a fifth location that contains data for a sensor that needs to be kept in sync.


### OpenCitySense

To make the complexities of sensor management more manageable, Fraunhofer IOSB started an internal research project to design the concept for a sensor management system, based on the OGC SensorThings API, and create an implementation of this system.

Since the [SensorThings API version 1.1](https://docs.ogc.org/is/18-088/18-088.html) is extendible by design, and already comes with several extensions, the architecture can be greatly simplified by using the SensorThings API service as the central data store for all sensor related data (figure 3).
This means that all components communicate through a single service, reducing the number of interconnects between components and reducing the spread of primary information across components.

The standard [tasking extension](https://docs.ogc.org/is/17-079r1/17-079r1.html) can be used to coordinate management actions between components, such as signalling to a connector that a sensor needs to be on-boarded, that a configuration needs to be changed, or that a sensor needs to be off-boarded.
The connector concept can then be extended to not just be a one-way ETL process, but to take an active role in the sensor registration process on the LoRaWAN stack.
It can receive information about new or updated sensors from the SensorThings service, and automatically take all required registration actions in the communication infrastructure.

Besides greatly simplifying the architecture, a second major advantage to using the SensorThing API service for all data storage is that it offers a consistent, powerful API for managing relational data.
This makes all data relevant for managing sensors and their data available in a unified, consistent way, and management tools or other clients do not need to implement multiple APIs.
While all publicly relevant sensor data and metadata can be stored in the core data model of the SensorThings API, internal management data can be stored in a custom data model extension.
Since this does not alter the core data model of the SensorThings API, clients implementing only the Sensing part will not be affected by this data model extension.

Sensor configuration parameters are modelled using the [SWE Common Data Model Encoding Standard](https://www.ogc.org/publications/standard/swecommon/), and translated by the connector into a form that the sensor understands.
This means that regardless of sensor brand or type, the management GUI can offer a consistent interface for changing sensor settings.

OpenCitySense consists of:

- A data model extension for FROST-Server.
- A GUI for managing sensors.
- A generic framework for developing connectors.
- A connector for connecting LoRaWAN devices over Chirpstack.
- A connector for connecting LoRaWAN devices over TTN/TTI.

OpenCitySense is a currently running internal research project of Fraunhofer IOSB, with the first demonstrators operational.

