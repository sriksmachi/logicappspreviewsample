# Logic Apps meet Azure Functions Runtime
Contains sample code for working with Logic Apps Preview

## About

Microsoft announced public preview of “Logic Apps Preview” runtime, this blog posts introduces you to key changes that Microsoft brings in this version of logic apps. I liked the direction it has taken, with this new set of features there are new possibilities for enterprise integration. 
At the end of the blog post there is a video in which I demo some of these new features. 
So, what has changed?
1.	The first critical thing is with Logic Apps Preview you can bundle the workflow and the runtime together. If you have worked on logic apps previously, you typically author logic apps on using the portal or on VS Code but end of the day they always run-on Azure Compute. Logic App preview allows you to design, build and run the logic app on your local machine as an executable or as a Docker container. The Azure logic Preview is built on a new portable runtime which is an extension of Azure Functions runtime (you will notice this in the video below as well). This change makes the logic app portal to any host which can run the Azure functions runtime like Windows or Linux machine or container orchestrator like K8s. 
2.	Logic Apps preview is single tenant. Previously the logic apps built by you share the compute, network, storage with other tenants of Azure. Logic Apps preview can run anywhere like on App Service using dedicated instances and the reason behind it should be obvious from the explanation above. This enhancement allows us to build isolated logic apps with custom compute, storage, and network configuration. 
3.	Logic Apps Preview support stateful and stateless orchestrations. Logic Apps (the current non-preview version) store the run history in memory, there is no storage associated with input/output of each activity within the orchestration. If you have worked on Azure durable functions earlier, you should be aware of the stateful orchestrations where the input/output of each action is stored in the external storage. Stateful workflows also improve the resiliency of the workflow, in case of an interruption the previous state can be reconstructed from the storage. They can also run up to a year. This enhancement makes logic apps a perfect fit for implementing resiliency cloud patterns like Subscriber, Agent, Supervisor pattern. The downside of this approach is the impact to the performance caused due to the latency for storing/retrieving data from storage.
4.	You can design, develop, test and deploy logic apps preview from VS Code with this extension. The below video is dedicated to this point. At this moment you can run this on Windows or MacOS only, but the runtime can be deployed on either Linux or Windows. 
5.	 Logics apps support 2 types of connectors, built-in correctors like recurrence schedule, HTTP Requests etc. and managed connectors like FTP, SFTP-SSH, Filesystem. Logic Apps Preview allows you to create your own custom connectors using this extension bundle.

## Demo 
The below video shows how you can design, develop, build, and deploy Logic Apps Preview as Docker Containers. 
https://youtu.be/bToDCXKHUBM
