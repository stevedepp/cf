## demo video for week 7 (video mislabled as 'week 6'): *CloudFormation Lambda Layers Command Line Tool Major Hiccup*     

Please click the video to hear sound or follow along with the transcript that's set just below the video.   

![demo](https://user-images.githubusercontent.com/38410965/111991926-38cf7600-8aeb-11eb-9e3b-7e12a30a90e3.mp4)

#

0

> Hi everyone.  Thank you for watching my video.   Last Monday, I was already at this point and apologies but I spent the week helping my twins fill in applications  to colleges. I've had some success with one major hiccup in using cloud formation and lambda layers to produce the architecture for a Serverless AI Data Engineering Pipeline.  I will spend 2 minutes walking you through how to use Lambda Layers and 2 minutes on cloud formation. JUST TO LET YOU KNOW: I will be switching from using terminal to using the ...

### CloudFormation  
### Lambda Layers  
### Command Line Tool   
### Major hiccup  

**Steve Depp**  
**MSDS 498 section 61**  

**Demo Video 7**  
**Serverless AI Data Engineering Pipeline**  
-	Lambda Layers  
-	CloudFormation   
-	debugging a work around  

**Different format**
-	terminal    
-	OS X file system  

<img width="682" alt="Last login" src="https://user-images.githubusercontent.com/38410965/113739052-6e6c8580-96cd-11eb-9944-2fd1aa92ae8d.png">

#

> ... OSX file viewer so you can see the file structure required for Lamdna Layers more clearly. Here is the file structure containing SHELL SCRIPTS for my command line tool that create Lambda Layers and build using Cloud Formation. I will briefly describe each: there’s a shell script to create an S3 bucket, ... 

### Easier to see Lambda Layers file structure

<img width="896" alt="1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113739021-6876a480-96cd-11eb-9d94-4a0b5eb135e6.png">

#

> ... a script to build the dependencies locally, ... 

### Build dependencies locally (MBP)

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739318-abd11300-96cd-11eb-9171-24d276ef4adf.png">

#

> ... and script to deploy a stack to AWS based on the cloud formation template.

### Deploy CloudFormation template to AWS

<img width="896" alt="3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113739492-dae78480-96cd-11eb-9a04-298a4a33e69f.png">

#

> There’s one lambda function 'serverlessproducer', ...

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739686-05394200-96ce-11eb-8644-b20d197aca4e.png">

#

> ... its requirements file, ...

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739793-213ce380-96ce-11eb-844b-b6a8ec53d067.png">

#

> ... and the folder of built dependencies which forms the half of our lambda layer that fulfils requirements for 'serverlessproducer' lambda, ... 

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739948-46c9ed00-96ce-11eb-9c4a-785da1dd5771.png">

#

> ... a second lambda function producerai, 

<img width="896" alt="ProducerAI" src="https://user-images.githubusercontent.com/38410965/113740130-6f51e700-96ce-11eb-97c2-369f286f96d2.png">

#

> ... its requirements file, ...

<img width="896" alt="ProducerAI" src="https://user-images.githubusercontent.com/38410965/113740250-87c20180-96ce-11eb-9f7c-fcea602bbdb6.png">

# 

> ... and the dependencies for producerai built. 

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113740387-a7592a00-96ce-11eb-9d3c-7a0eaf7e76df.png">

#

> finally there’s the blueprint template file for cloud formation  

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113740529-c657bc00-96ce-11eb-9220-110f3a16335c.png">

#

> Now I will walk you through CLT scripts that build layers and architecture. This shell script creates a bucket to hold lambdas and their layer dependencies.  

<img width="896" alt="1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113740726-f737f100-96ce-11eb-8942-af326e6f5fa8.png">

#

> First, it makes a random number, ...

<img width="817" alt="@1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113740782-028b1c80-96cf-11eb-9360-45acbba01d01.png">

#

> ... attaches that number to the bucket name “lambda-artifacts”  making the name unique, ...

<img width="817" alt="@ 1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113740961-3403e800-96cf-11eb-8e59-3ebb6a0fe8c3.png">

#

> ... stores that name in a file, ...

<img width="817" alt="0 1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113741102-4f6ef300-96cf-11eb-88bd-3dc9a2301a61.png">

#

> ... and makes a bucket.

<img width="817" alt="@ 1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113741158-5f86d280-96cf-11eb-857b-313790d6fc4a.png">

# 

> The build script ...

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113741339-88a76300-96cf-11eb-8cd3-15a8faae9369.png">

#

> ... sets itself up so that gathering requirements will be loud in case is an error.

<img width="817" alt="B 1 #1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113741390-96f57f00-96cf-11eb-953a-22d460b66751.png">

#

> It removes any previous packaged dependenciy folders, ...

<img width="817" alt="BB 1 @1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113741544-c2786980-96cf-11eb-8248-534f674cfdef.png">

#

> ... and installs new ones. And now we are ready to ...

<img width="817" alt="2-build-layer sh" src="https://user-images.githubusercontent.com/38410965/113741591-cc9a6800-96cf-11eb-81ab-a57592ad9da5.png">

#

> deploy. 

<img width="896" alt="3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113741744-f2c00800-96cf-11eb-9715-66cb43d4ec2f.png">

#

> This shell script ...

<img width="817" alt="3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113741782-fce20680-96cf-11eb-9110-463797f75db9.png">

#

> ... transforms ...








