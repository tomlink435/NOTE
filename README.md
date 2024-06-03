Week 1: 
App Service Overview (quick start, create a simple app service)
[Important]Understand App Service Architecture:https://docs.microsoft.com/en-us/archive/msdn-magazine/2017/february/azure-inside-the-azure-app-service-architecture  
What is PaaS platform, compare it with IaaS
[Important]Understand App Service Plan :
https://docs.microsoft.com/en-us/azure/app-service/overview-hosting-plans 
https://docs.microsoft.com/en-us/azure/app-service/overview  
[Important]Understand App Service Sandbox: https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox 
[Important] https://docs.microsoft.com/en-us/azure/app-service/operating-system-functionality 

Deploy App Service:Run your app from a ZIP package - Azure App Service | Microsoft Docs
	[Important] Run from package
	[Important] Deploy Zip or war 
	[Important] Github Actions
	[Important] Deploy via DevOps/Azure Pipeline 
File structure on azure · projectkudu/kudu Wiki (github.com) 
Kudu architecture · projectkudu/kudu Wiki (github.com)
Deployment credentials · projectkudu/kudu Wiki (github.com)
Accessing files via ftp · projectkudu/kudu Wiki (github.com)

Lab:
	• Learn the differences between different app service plan tiers. Create and deploy a .NET Core Azure web app with two deployment slots on a standard App Service Plan. 
	• Check the new app on Azure portal and understand these concepts: web app name, app service plan name, resource group, location, stamp, host name. 
	• Understand App Service inbound and outbound Ips. 
	• How to force users to access a website over https protocol? (two methods: configure it on Azure portal or set rules in web.config) 
	• [Important]Get familiar with Kudu site (Advanced tool). 
	• Modify web app's web.config from  kudu site: how to redirect all http requests to https and how to redirect all requests from <customdomain>.com to [http://www.%3Ccustomdomain%3E.com/]www.<customdomain>.com 
	• Drag & drop files from local machine to Kudu Debug Console 
	https://blogs.msdn.microsoft.com/benjaminperkins/2017/12/28/deploy-to-an-azure-app-service-using-kudu-and-a-zip-file/ 
	https://blogs.msdn.microsoft.com/benjaminperkins/2017/11/29/drag-and-drop-deployment-to-an-azure-app-service-quick-for-simple-small-changes/ 

Week2:
 Management 	Configure	Configure apps - Azure App Service | Microsoft Docs
Configure Linux Python apps - Azure App Service | Microsoft Docs
  		Back up an app - Azure App Service | Microsoft Docs
	Backup & Restore 	Restore app from backup - Azure App Service | Microsoft Docs
		Restore deleted apps - Azure App Service | Microsoft Docs
		
 	Clone 	https://docs.microsoft.com/en-us/azure/app-service/app-service-web-app-cloning 
		 
 	Monitor 	Monitor App Service with Azure Monitor - Azure App Service | Microsoft Docs
		Enable diagnostics logging - Azure App Service | Microsoft Docs
		Monitor the health of App Service instances - Azure App Service | Microsoft Docs
 	Scale 	Scale up features and capacities - Azure App Service | Microsoft Docs
 		Get started with autoscale in Azure - Azure Monitor | Microsoft Docs
		
 	Slot & Swap 	Set up staging environments - Azure App Service | Microsoft Docs


Secure	 	 
	Domain	Tutorial: Map existing custom DNS name - Azure App Service | Microsoft Docs
		Buy a custom domain name - Azure App Service | Microsoft Docs
		
  	SSL	Secure a custom DNS with a TLS/SSL binding - Azure App Service | Microsoft Docs
		Add and manage TLS/SSL certificates - Azure App Service | Microsoft Docs
		Use a TLS/SSL certificate in code - Azure App Service | Microsoft Docs
		Understand the meanings of DNS resolution, DNS records, DNS propagation, SSL certificate, and difference between http and https.
 	Managed Identity	Managed identities - Azure App Service | Microsoft Docs
		Tutorial - .NET Web app accesses storage by using managed identities - Azure App Service | Microsoft Docs
 	Key Vault Reference	Use Key Vault references - Azure App Service | Microsoft Docs
	CORS	Consume an API app from JavaScript using CORS
 		
 Network
		Networking features - Azure App Service | Microsoft Docs
		https://docs.microsoft.com/en-us/azure/app-service/app-service-ip-restrictions 
Inbound/Outbound IP addresses - Azure App Service | Microsoft Docs
		Connect privately to an Azure Web App using Private Endpoint | Microsoft Docs
		Integrate your app with an Azure virtual network - Azure App Service | Microsoft Docs
		

Week 3:
ASE 	 	 
 	Introduction to App Service Environment 	https://docs.microsoft.com/en-us/azure/app-service/environment/intro 
		
Performance		
	Local Cache	https://docs.microsoft.com/en-us/azure/app-service/overview-local-cache 
	Understand SNAT	https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections
		
		https://4lowtherabbit.github.io/blogs/2019/10/SNAT/ 
	Diagnostic / Auto-heal	Diagnostics and solve tool - Azure App Service | Microsoft Docs 
		Auto-healing 
		Demystifying the magic behind App Service OS updates
Function		Azure Functions documentation | Microsoft Docs
	About Azure Functions	
	Azure Functions hosting options	
	Quickstart: Create a function in Azure with Python using Visual Studio Code	
	Connect to storage: VS CODE	
	Azure Functions runtime versions overview	
	Hosting and scale	
	Deployment technologies in Azure Functions	
	Events and messaging: Event-driven scaling in Azure Functions, Concurrency in Azure Functions	
	Trigger and bindings	
	Monitoring 	
	Consumption plan costs	
	IP addresses	
	Languages: Python	
	Networking options	
		
	Developer Guide	
	Develop and debug locally	
	Visual Studio Code Development	
	Use dependency injection in .NET Azure Functions	
	Manage connections in Azure Functions	
	Azure Functions error handling and retries	
	Manually run a non HTTP-triggered function	
		
	Deploy: build and deploy using Azure Pipeline, Zip Deployment, Run from package	
		
	Configure: Managed a function app, set the runtime version, disable a function	
		
	Configure monitoring	
	Streaming logs	
	Analyze telemetry data	
		
	Secure: Add SSL cert, Restrict Ips, managed identity, Reference secrets from key vault 	
		
	Troubleshoot: Python functions: General troubleshooting	
		
	Reference: Triggers and bindings : Service Bus, HTTP and webhooks, Timer	
		

Week 4.
Vertical 	Topics 	Docs 
OSS 	Docker Overview 	Docker overview | Docker Documentation
		https://docs.docker.com/get-started/ 
		
		
 	Web App/Function For Containers 	Overview on Web App for Containers and Azure App Service on Linux
		Run a custom container in Azure
		Migrate custom software to Azure App Service using a custom container
		Configure a custom container for Azure App Service
		Create a function on Linux using a custom container
		App Service on Linux FAQ | Microsoft Docs
		
 	Linux Commands	
		
WebJob		
	Run background tasks with WebJobs in Azure App Service	Run background tasks with WebJobs - Azure App Service | Microsoft Docs
	WebJobs	WebJobs · projectkudu/kudu Wiki (github.com)

azure static web app
https://docs.microsoft.com/en-us/azure/static-web-apps/
 
Azure app configuration.
https://docs.microsoft.com/en-us/azure/azure-app-configuration/overview
 

![image](https://github.com/tomlink435/NOTE/assets/99723188/80ffd121-95d0-4aa4-86fc-c651f6b7a754)



Introducing Azure Functions
Languages and runtimes
Best Case Connectivity Coding Patterns
Create and deploy an Azure Function
WebJobs
Authentication and authorization
KUDU Deployment
Azure Resource Management (ARM) templates
Azure Monitor overview
Azure Functions Overview
Azure Compute Options
Hosting Plans / Runtimes / Languages
Triggers and Bindings concepts
How to execute an Azure Function with triggers
5 things about Azure Functions (Video)
The introduction to Azure Functions (Video)
Azure Functions and Serverless architectures (Video)
Azure Functions developers guide
Azure Functions error handling
Manage connections in Azure Functions
Create Azure Function (JavaScript)
Create Azure Function (C# / Visual Studio)
Create Azure Function (C# / Azure Portal)
Create Azure Function (Timer Trigger / Portal)
Developing Azure Functions (Video)
Deploy to Azure with Azure App Service
Managing a function app
What are Durable Functions
Durable Functions Workflows (Video)
Introducing Azure Functions
Languages and runtimes
Best Case Connectivity Coding Patterns
Create and deploy an Azure Function
WebJobs
Authentication and authorization
KUDU Deployment
Azure Resource Management (ARM) templates
Azure Monitor overview
Azure Functions Overview
Azure Compute Options
Hosting Plans / Runtimes / Languages
Triggers and Bindings concepts
How to execute an Azure Function with triggers
5 things about Azure Functions (Video)
The introduction to Azure Functions (Video)
Azure Functions and Serverless architectures (Video)
Azure Functions developers guide
Azure Functions error handling
Manage connections in Azure Functions
Create Azure Function (JavaScript)
Create Azure Function (C# / Visual Studio)
Create Azure Function (C# / Azure Portal)
Create Azure Function (Timer Trigger / Portal)
Developing Azure Functions (Video)
Deploy to Azure with Azure App Service
Managing a function app
What are Durable Functions
Durable Functions Workflows (Video)

![image](https://github.com/tomlink435/NOTE/assets/99723188/c8cf582f-5fd1-4fcf-8532-18d22cc3a79a)

