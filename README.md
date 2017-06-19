# The Acme Freight Journey

Acme Freight Shipping is a fictional shipping and logistics company using the [Logistics Wizard](https://github.com/ibm-bluemix/logistics-wizard) application framework to reimagine supply chain optimization systems for the 21st century.

Acme Freight uses an application, called [Logistic Wizard](https://github.com/ibm-bluemix/logistics-wizard) to manage some of its assets. The application is composed of several microservices, including three Cloud Foundry applications and multiple OpenWhisk actions.

Acme Freight uses LoopBack, an open source Node.js framework, built for quickly creating and exposing APIs for new and existing applications and data. LoopBack enables Acme Freight to create an application that integrates with their existing ERP system, and API Connect allows them to expose data via a managed API.

*For more on the Acme Freight journey and the technologies behind it, [visit the Acme Freight journey website](http://developer.ibm.com/code/journey/unlock-enterprise-data-using-apis?cm_mmc=github-code-_-native-_-acme-_-journey&cm_mmca1=000019RT&cm_mmca2=10004796).*

## Acme Freight Tutorials

To start learning more about Acme Freight and the technology behind it, jump to one of the tutorials below.

### Deploy Acme Freight
* [Deploy your own Acme Freight with IBM DevOps Toolchain](TOOLCHAIN-README.md) 
> [![Deploy To Bluemix](./.bluemix/create_toolchain_button.png)](https://console.ng.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fsvennam92%2Facme-freight.git&cm_mmc=github-readme--native-_-acme-_-create-toolchain&cm_mmca1=000019RT&cm_mmca2=10004796)

### Rapidly Create APIs with the Node API Framework, LoopBack 
* [Use LoopBack and API Connect to rapidly expose ERP data with APIs](APIC-ERP-README.md) 

### Create secured APIs for OpenWhisk actions in just a few clicks
* [Create secured APIs for your OpenWhisk actions on Bluemix](OW-NAPI-README.md) 

## Acme Freight Overview
The video below demonstates how Acme Freight Shipping used the Logistics Wizard framework, along with IBM API Connect, to deliver an application allowing them to revolutionize the agility of their supply chain.

[![](docs/acme-vid.png)](https://www.youtube.com/watch?v=R1KCrJAXLvA)


## Acme Freight Architecture
![](acme-architecture.png)

The following projects are leveraged in the overall Acme Freight solution:

* [acme-freight-erp](https://github.com/ibm/acme-freight-erp) - defines the API used by Acme Freight to access data from an ERP system. It also provides a default implementation to be used as a simulator. The simulator is a Node.js application connected to a PostgreSQL database. Through its API, it manages users (supply chain managers and retail store managers), distribution centers, retail stores and shipments.

* [acme-freight-webui](https://github.com/ibm/acme-freight-webui) - provides a dashboard to view ongoing shipments and alerts. There is no log-in or user credentials per se to use the deployed applications. Instead a unique demo ID is assigned to any new user trying the application. Behind each demo ID, Acme Freight creates an isolated environment with a default set of business users, distribution centers, retail stores, shipments. Refer to the [walkthrough](WALKTHROUGH.md) to get a tour of the capabilities.

* [acme-freight-recommendation](https://github.com/ibm/acme-freight-recommendation) - makes shipment recommendations based on weather conditions. It is a set of Bluemix OpenWhisk to retrieve current weather conditions and given a weather event to generate new shipment recommendations. These recommendations could then be turned into real orders.

* [acme-freight-controller](https://github.com/ibm/acme-freight-controller) - acts as the main controller for interaction between the services. It receives requests from the user interface and routes them to the ERP or the weather recommendation module.

*Acme Freight is forked and extended from the IBM Bluemix project, Logistics Wizard. Visit the Logistics Wizard project [wiki](https://github.com/IBM-Bluemix/logistics-wizard/wiki) for a detailed breakdown of the original Logicistics Wizard architecture and deployment strategy.*


## Resources
- [The Acme Freight Journey](http://developer.ibm.com/code/journey/unlock-enterprise-data-using-apis?cm_mmc=github-code-_-native-_-acme-_-journey&cm_mmca1=000019RT&cm_mmca2=10004796)
- [Unlock Enterprise Data with LoopBack](https://developer.ibm.com/code/2017/05/04/unlock-enterprise-data-with-loopback?cm_mmc=github-code-_-native-_-acme-_-related-content&cm_mmca1=000019RT&cm_mmca2=10004796)


## License

See [LICENSE](LICENSE) for license information.

