# WEB STACK IMPLEMENTATION

## WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS

A technology stack is a set of frameworks and tools used to develop a software product. This set of frameworks and tools are very specifically chosen to work together in creating a well-functioning software.

Firstly, I created an EC2 in Asia Pacific region Tokyo.

Let me list certain parameters when choosing an AWS region which factors should you consider:

* Latency and proximity

* Security and regulatory compliance

* Service Level Agreements (SLA)

And finally, the most important is the **cost**

<img width="404" alt="Asia pacific" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/f6d6d45a-049e-4ff9-b637-fc9cf3fa2079">


### Click on "Services" at the upper left corner and you will see the all the Services available on AWS. Click on "EC2"

<img width="542" alt="ec2" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/4a8ed69a-6dd6-4d08-b235-77250c69477b">

## select ec2 stroll down, and Click on "Launch Instance."

<img width="890" alt="launch ins" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/6c617226-062e-403b-a83e-ca6cf1feb007">



## Click on Next: to choose an instance type

<img width="605" alt="instance type" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/d2c113e3-4639-4273-b0a3-886cb5fbfd3d">

## Next: Select a keypair

<img width="625" alt="keypair " src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/3e4a7d1f-74b9-40ff-bbdb-2450b309f6c0">

## Next: Configure Instance Details by creating or adding an existing security group

<img width="590" alt="Screenshot 2023-06-05 075828" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/e00e00ed-92fb-4852-b47f-89961cd2388d">

**Next:**  Add Storage; to add or configure the Storage size and type. Every time you launch an instance from an AMI, a root storage device is created for that instance. The root storage device contains all the information necessary to boot the instance. You can specify storage volumes in addition to the root device volume when you create an AMI or launch an instance using block device.

<img width="602" alt="Screenshot 2023-06-05 080038" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/871f336d-8b1f-4966-aa4b-d5769f70a36c">

The next phase is to view your instance state, click on your instance to view it. At this stage, you will see if your instance is running or still pending. mine is running, now i can view my instance details

<img width="1262" alt="Screenshot 2023-06-05 080702" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/51c16be6-8ba1-482e-a09b-cdd71a33ca30">

**Next** I opened my MOBAXTERM, choose Ubuntu-22.04. 

<img width="1277" alt="Screenshot 2023-06-05 081921" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/28751386-b9bb-4f25-a4e4-f5cb10f2cea2">

**Next**: Although, I have my keypair stored in a folder named **soso** I cd into the folder **soso** then connect to the instance using the link

<img width="699" alt="Screenshot 2023-06-05 082703" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/9e9e4ce2-bbc2-4ffc-ab6d-51140cdd88be">


<img width="1262" alt="Screenshot 2023-06-05 082844" src="https://github.com/Nosa213/My-Devops-Project-1/assets/125190958/20e597b6-335f-4794-81ca-1f0f03c826fc">










