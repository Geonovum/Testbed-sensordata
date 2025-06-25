# Conclusion
Geonovum started this testbed in order to explore how OGC sensor standards can help the Dutch public sector better organize and leverage their sensordata.
This testbed is a first step into exploring whether there is value in making one or more of these standards mandatory within the Dutch public sector.
The testbed certainly has provided new insights and ideas on how to further our investigations. We will summarize these here from Geonovum's perspective.

## Suitability Sensordata Standards for Dutch public sector
To Geonovum the work in research question 1 "Communicating with a collection of sensors" has shown there can be great utility in achieving more interoperability between sensors on the one hand, and applications used for sensordata gathering and analysis on the other. The standards were very much applicable to the usecases in this testbed, but would likely also extend to similar usecases such as water quality based sensor networks. The usecase from Rotterdam contained water levels. However, Dutch public sector stakeholders such as the [Informatiehuis Water](https://www.ihw.nl/) and the [Waterschapshuis](https://www.hetwaterschapshuis.nl/) would also need to be involved in any future discussion about mandatory standards for sensordata.

However, implementation of the standards within existing software for collecting sensordata from (a large number of) individual sensors is certainly not trivial and there are issues that need to be addressed before making one or more of these standards mandatory becomes a viable option. To Geonovum, the most important lesson is that the internal data model of the Nelen & Schuurmans application (Lizard) is not easily mapped to the OMS based model of SensorThings API. According to Nelen & Schuurmans their competitors also use similar internal data models. This warrents further investigation, involving these suppliers, in order to find solutions to overcome this issue.

Research question 2 "Visualization & analysis" has shown, in Geonovum's opinion, that Sensorthings API is easily integrated into client applications that want to visualize sensordata. This certainly makes the case for SensorThings API as an interoberable mandatory standard for exposing (large) collections of sensordata a strong one. Visualization and dashboarding are of course not the only things clients would like to do with sensordata. Further investigation into other client usecases seems warrented, such as integration within tooling used by Data Scientists (Jupyter Notebook, Excel, Matlab etc...). Another point is that we only investigated Sensorthings API in this research question. Connected systems API should in theory also work well, as it can be an extension of [OGC API Features](https://ogcapi.ogc.org/features/) (which is already a mandatory standard for the Dutch public sector). Connected Systems API should be especially suitable for usecases where sensordata is combined with other geospatial features.

The final issue we investigated in research question 3 "Initial device registration". As noted by Fraunhofer, this is a problem not just for sensors but for devices in general. The manufacturer cannot know in advance what these sensors and other devices will be used for as there are many different usecases and scenario's in which they can be employed. As Geonovum, we were pleasently surprised that Fraunhofer was already working towards a solution and was able to contribute a lot to the testbed. Although this is not a finished solution yet as demonstrated in the testbed, it holds promise to greatly simplify onboarding and management of sensor networks. Geonovum expects this could, when mature enough, become a standardized extension to the OGC SensorThings API standard.A hands-on trial with several stakeholders from the Dutch public sector is a logical next step.

# Future work
As Geonovum we want to initiate the following follow-up actions now that the Testbed has ended:

* Investigate the mapping issue further with Nelen & Schuurmans and their competitors. Can we find solutions that are acceptable and would make a mandatory standard for sensordata Feasible?

* Discuss the results of the testbed with a broader group of stakeholders and at the very least Informatiehuis Water and the Waterschapshuis.

* Test the suitability of SensorThings API and Connected Systems API for use in data science applications.

* Test the suitability of Connected Systems API for dashboards and visualization.

* Do a hands-on trial with initial device registration together with stakeholders from the Dutch public sector using our own sensors.

If you read this report, are from the Dutch public sector and you have additional issues you would like to investigate or discuss with us, please contact Geonovum. All testbed implementations will remain available until at least the end of October 2025. 
