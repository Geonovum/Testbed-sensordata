# Conclusion
Geonovum started this testbed to explore how OGC sensor standards can help the Dutch public sector better organize and leverage their sensordata.
This testbed is a first step into exploring wether there is value in making one or more of these standards mandatory within the Dutch public sector.
The testbed certainly has provided new insights and idea's on how to further our investigations. We will summurize these here from Geonovums perspective.

## Suitability Sensordata Standards for Dutch public sector
To Geonovum the work in research question 1 "Communicating with a collection of sensors" has shown there can be great utility in achieving more interoperability between sensors and applications used for sensordata gathering and analysis. The standards were very much applicable to the usecases in this testbed, but would likely also extend to similar usecases such as water quality based sensornetworks. The usecase from Rotterdam contained waterlevels. However the Informatiehuis Water and het Waterschapshuis would also need to be involved in any future discussion about mandotory standards for sensordata.
However implementation of the standards within existing software for collecting sensordata from (a large number of) individual sensors is certainly not trivial and there are issues that need to be adressed before making one or more of these standards mandatory becomes a viable option. To geonovum the most important lesson is that the internal data model of the Nelen & Schuurmans application (Lizard) is not easily mapped to the OMS based model of sensorthings API. According to Nelen & Schuurmans their competitors also use similar internal data models. This warrents further investigation with these suppliers and what solutions can be found to overcome this issue.

Research question 2 "Visualization & analysis" has shown in Geonovums opinion that Sensorthings API is easily integrated into client applications that want to visualize sensordata. This certainly makes the case for sensorthings API as an interoberable mandatory standard for exposing (large) collections of sensordata a strong one. Visualization and dashboarding are of course not the only things clients would like to do with sensordata. Further investigation into other client usecases seems warrented such as integration within tooling used by Data Scientists (Jupyter Notebook, Excel, Matlab etc...). We also only investigated Sensorthings API in this research question. Connected systems API should in theory also work well as it can be an extension of OGC API Features and should especially be suitable for usecases where sensordata is combined with other geospatial features.

The final issue we investigated in research question 3 "Initial device registration". As noted by Fraunhofer, this is problem not just for sensors but for devices in general where the manufacturer cannot know what it will be used for as there are many different usecases and scenario's in which they can be employed. As Geonovum we were pleasently surprised that Fraunhofer was already working towards a solution. Allthough this is not a finished solution yet as demonstrated in the testbed it holds promise to greatly simplify onboarding and management of sensornetworks. A hands on trial with several stakeholders from the Dutch public sector is a logical next step.

# Future work
As Geonovum we want to initiate the following follow-up actions now that the Testbed has ended:

* Investigate the mapping issue further with Nelen & Schuurmans and their competitors. Can we find solutions that are acceptable and would make a mandatory standard for sensordata Feasible.

* Discuss the results of the testbed with a broader group of stakeholders and at the very least Informatiehuis Water and het waterschapshuis.

* Test the suitability Of sensorthings API and connected systems API for use in data science applications.

* Test the suitability of connected systems API for dashboards and visualization

* Do a hands on trial with initial device registration together with stakeholders from the dutch public sector using our own sensors.

If you read this report and you are from the Dutch public sector and you have additional issues you would like to investigate or discuss with us, please contact Geonovum. All testbed implementations will remain available until at least the end of October. 
