# Red Dog Demo - AKS Deployment

## Background

This repository leverages the [reddog applicaton codebase](https://github.com/Azure/reddog-code) and was created to help users deploy a comprehensive, microservice-based sample application to Azure. 


## Getting Started

This repo contains the scripts and configurations to deploy the Red Dog Demo along with the backing Azure Resources. Simply clone the repo and execute the `run.sh` deployment script.


## Architecture

> Need to update based on AKS deployment. 

![Architecture diagram](assets/reddog_architecture.png)

This repository leverages bicep templates in order to execute the deployment of the Reddog applicaton and the supporting Azure Infrastructure. Bicep is a Domain Specific Language (DSL) for deploying Azure resources declaratively and provides a transparent abstraction over ARM and ARM templates.  

### Infrastructure Components

#### Resource Group
A logical container which holds all resources needed to run the above solution in Azure

#### AKS Cluster
The application microservices will run in this cluster

#### Azure Cosmos DB 
Microsoft's NoSQL multi-model managed database as a service offering which is used as the Dapr State Store component implementation for the Loyalty Service

#### Azure Cache for Redis 
A distributed, in-memory, scalable solution providing super-fast data access which is used as the Dapr State Store component implementation for the Makeline Service

#### Azure Service Bus 
A fully managed enterprise message broker with message queues and publish-subscribe topics used as the Dapr PubSub component implementation. This component is leveraged by multiple services, with the Order Service publishing messages to four other services in the application: Makelike, Accounting, Loyalty and Receipt

#### Azure SQL DB 
A member of the Azure SQL family, Azure SQL supports modern cloud applications on an intelligent, managed database service. This resource is created for the Accounting Service, which makes use of EF Core for interfacing with the DB. 

#### Azure Blob Storage 
Azuree Blob storage is optimized for storing massive amounts of unstructured data. Unstructured data is data that doesn't adhere to a particular data model or definition, such as text or binary data. Blob storage is used by the Receipt Service via Dapr Output Bindings to store order receipts.


## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.