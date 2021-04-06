## demo video for week 7 (video mislabled as 'week 6'): *CloudFormation Lambda Layers Command Line Tool Major Hiccup*     

Please click the video to hear sound or follow along with the transcript that's set just below the video.   

![demo](https://user-images.githubusercontent.com/38410965/111991926-38cf7600-8aeb-11eb-9e3b-7e12a30a90e3.mp4)

#

0

> Hi everyone.  Thank you for watching my video.   Last Monday, I was already at this point, and apologies, but I spent the week helping my twins fill in applications  to colleges. I've had some success with one major hiccup in using Cloud Formation and Lambda Layers to produce the architecture for a Serverless AI Data Engineering Pipeline.  I will spend 2 minutes walking you through how to use Lambda Layers and 2 minutes on Cloud Formation. JUST TO LET YOU KNOW: I will be switching from using terminal to using the ...

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

> ... OSX file viewer so you can see the file structure required for Lambda Layers more clearly. Here is the file structure containing SHELL SCRIPTS for my command line tool that create Lambda Layers and build using Cloud Formation. I will briefly describe each: there’s a shell script to create an S3 bucket, ... 

### Easier to see Lambda Layers file structure

<img width="896" alt="1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113739021-6876a480-96cd-11eb-9d94-4a0b5eb135e6.png">

#

> ... a script to build the dependencies locally, ... 

### Build dependencies locally (MBP)

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739318-abd11300-96cd-11eb-9171-24d276ef4adf.png">

#

> ... and script to deploy a stack to AWS based on the Cloud Formation template.

### Deploy CloudFormation template to AWS

<img width="896" alt="3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113739492-dae78480-96cd-11eb-9a04-298a4a33e69f.png">

#

> There’s one lambda function 'serverlessproducer', ...

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739686-05394200-96ce-11eb-8644-b20d197aca4e.png">

#

> ... its requirements file, ...

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739793-213ce380-96ce-11eb-844b-b6a8ec53d067.png">

#

> ... and the folder of built dependencies which forms the half of our Lambda Layer that fulfills requirements for 'serverlessproducer' Lambda, ... 

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113739948-46c9ed00-96ce-11eb-9c4a-785da1dd5771.png">

#

> ... a second Lambda function 'producerai', 

<img width="896" alt="ProducerAI" src="https://user-images.githubusercontent.com/38410965/113740130-6f51e700-96ce-11eb-97c2-369f286f96d2.png">

#

> ... its requirements file, ...

<img width="896" alt="ProducerAI" src="https://user-images.githubusercontent.com/38410965/113740250-87c20180-96ce-11eb-9f7c-fcea602bbdb6.png">

# 

> ... and the dependencies for 'producerai' built. 

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113740387-a7592a00-96ce-11eb-9d3c-7a0eaf7e76df.png">

#

> finally there’s the blueprint template file for Cloud Formation.  

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113740529-c657bc00-96ce-11eb-9220-110f3a16335c.png">

#

> Now, I will walk you through CLT scripts that build layers and architecture. This shell script creates a bucket to hold Lambdas and their layer dependencies.  

<img width="896" alt="1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113740726-f737f100-96ce-11eb-8942-af326e6f5fa8.png">

#

> First, it makes a random number, ...

<img width="817" alt="@1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113740782-028b1c80-96cf-11eb-9360-45acbba01d01.png">

#

> ... attaches that number to the bucket name 'lambda-artifacts'  making the name unique, ...

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

> It removes any previous packaged dependency folders, ...

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

<img width="817" alt="# 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113742462-a7f2c000-96d0-11eb-9a9f-16a5b7365c4f.png">

#

> ... a template file called 'template.yaml' into ...

<img width="817" alt="@ 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113742514-b0e39180-96d0-11eb-92e2-5875b57f87f3.png">

#

> ... a new template file called 'out.yml'.

<img width="817" alt="3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113742562-ba6cf980-96d0-11eb-9984-c4b08fe6589a.png">

#

> Here’s the original 'template.yml' file; which incorporates a Lambda Layers feature called 'transforms'.  Transforms are like an Excel macro for automation.  

<img width="817" alt="@1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113742739-ebe5c500-96d0-11eb-9744-084cab7f0c1a.png">

#

> You start with 'template.yml', with references to code for the lambda function, 'serverlessproducer' on my MBP, ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113742792-f7d18700-96d0-11eb-830f-3a1683c77440.png">

#

> ... and depdenencies in the folder named 'packageServerlessProducer' also on my MBP.

<img width="817" alt="@1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113743083-4121d680-96d1-11eb-9823-77ee7997778f.png">

#

> The same here for 'producerai' Lambda code with a reference to my MBP, ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113743230-6d3d5780-96d1-11eb-8c5c-4bcfa0f55cbb.png">

#

> ... and its folder full of dependencies - this path is also on my MBP.

<img width="817" alt="@1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113743248-775f5600-96d1-11eb-9cbb-0b5c3b9f51de.png">

#

> The automation yields a transformed template 'out.yml' with new addresses for resource files on the S3 bucket we made earlier.    

<img width="817" alt=" 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113743470-b7bed400-96d1-11eb-95f7-c9d3406ddf3a.png">

#

> Here’s the 'out.yml' referring to the S3 bucket holding the code for 'severlessproducer' Lambda, ...

<img width="819" alt="out 9 51 31 PM yml" src="https://user-images.githubusercontent.com/38410965/113743536-c60cf000-96d1-11eb-91c3-a7e285398528.png">

#

> ... its dependencies,  ...

<img width="819" alt="( out 9 51 31 PM yml" src="https://user-images.githubusercontent.com/38410965/113743725-fce30600-96d1-11eb-8bd4-9b72b8f25ccb.png">

#

> ... 'producerai' code, ...

<img width="819" alt="( out 9 51 31 PM yml" src="https://user-images.githubusercontent.com/38410965/113746481-5f3d0600-96d4-11eb-8758-4bfbaa9a8cff.png">


#

> ... and its dependencies.

<img width="819" alt="( out 9 51 31 PM yml" src="https://user-images.githubusercontent.com/38410965/113746505-682dd780-96d4-11eb-9ed5-8dd17372152c.png">


#

> So, now after this script, we have 'out.yaml', that has only folders addresses for resources found in an S3 bucket. 

<img width="817" alt="aws cloudformation deploy --template-file out yml --stack-name blank-python" src="https://user-images.githubusercontent.com/38410965/113746558-73810300-96d4-11eb-97e0-63dc4e6c6752.png">


#

> Next, we ...

<img width="817" alt="@ 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113746589-7bd93e00-96d4-11eb-8004-82b0c40f1ac4.png">

#

> ... deploy.

<img width="817" alt=" 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113746622-872c6980-96d4-11eb-957f-bbebd81e7397.png">

#

> ... the 'out.yml' file ...

<img width="817" alt="© 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113749051-2fdbc880-96d7-11eb-89d2-91baf513998d.png">

#

> ... to build a stack called 'blank.python'.

<img width="817" alt=" 3-deploy sh" src="https://user-images.githubusercontent.com/38410965/113749087-3b2ef400-96d7-11eb-8d95-60960c639747.png">

#

> Now, I will walk you through the Cloud Formation template to show you how the architecture ...

<img width="896" alt="• Search" src="https://user-images.githubusercontent.com/38410965/113749418-a678c600-96d7-11eb-8dee-a3db74c0b0e0.png">

#

> ... gets data from DynamoDB table named 'fang' ...

<img width="817" alt="template yml - Edited" src="https://user-images.githubusercontent.com/38410965/113749464-b1cbf180-96d7-11eb-9543-085b816ac1b7.png">

#

> ... through and SQS queue named 'producer' ...

<img width="817" alt="w template yml - Edited" src="https://user-images.githubusercontent.com/38410965/113749511-b8f2ff80-96d7-11eb-9ac3-c2c076dfb7d8.png">

#

> ... into an S3 bucket named 'fangsentiment-depp'.

<img width="817" alt="AccessControl PublicRead" src="https://user-images.githubusercontent.com/38410965/113749553-c0b2a400-96d7-11eb-8d23-47ab52f02625.png">

#

> We start with 'serverlessproducer', ...

<img width="817" alt="Description Dependencies for the blank-python" src="https://user-images.githubusercontent.com/38410965/113749933-328aed80-96d8-11eb-8d21-6730522308e5.png">

#

> ... and its dependencies, ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113749965-39b1fb80-96d8-11eb-9814-fd43cbb511fd.png">

#

> ... pick up from 'fang' ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113750019-446c9080-96d8-11eb-8bda-99227375de08.png">

#

> ... deposit in SQS queue named 'producer' ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113750102-5d754180-96d8-11eb-99f9-05007993d46a.png">

#

> ... on a rule to do so every 5 minutes.

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113750124-6534e600-96d8-11eb-934d-29c31ce27d1c.png">

#

> Then, 'producerai' Lambda ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113750387-b9d86100-96d8-11eb-8667-d4799fae9702.png">

#

> ... and its dependencies ...

<img width="817" alt="template yml" src="https://user-images.githubusercontent.com/38410965/113750442-c78de680-96d8-11eb-905f-ca507210c062.png">

#

> ... pick that data up from the SQS queue named 'producer' ...

<img width="817" alt="w template yml -  Edited" src="https://user-images.githubusercontent.com/38410965/113750474-d2487b80-96d8-11eb-8053-12d3a41fff1c.png">

# 

> ... and deliver processed data to the S3 bucket named 'fangsentiment-depp' ...

<img width="817" alt="1-create-bucket sh" src="https://user-images.githubusercontent.com/38410965/113750489-db394d00-96d8-11eb-9b0e-13ec8c86c9f4.png">

#

> ... as governed by a event source mapping between 'producer' SQS and 'producerai' Lambda.

<img width="817" alt="template yml - Edited" src="https://user-images.githubusercontent.com/38410965/113750519-e7bda580-96d8-11eb-89e4-bd182aea6cf4.png">

#

> Hiccup is that numpy is c, and a c is picky about which OS you're using, and so won’t take a MAC OSX version of numpy to fulfill the dependency for pandas on Amazon linux.

### Hiccup

numpy is c and required by pandas which is a requirement of 'producerai' Lambda  
https://github.com/numpy/numpy/issues/13465

#

> Workaround involved lots of testing and eventually some success using AWS Cloud9 to build the right numpy file.  Thank you for watching.  And if you have any ideas on how to fulfill this numpy situation without an artificial workaround, please let me know. 

### Workarounds

**tried:**  
	pip install —platform linux numpy  
https://stackoverflow.com/questions/45980037/how-to-download-pip-packages-for-a-different-operating-system

https://stackoverflow.com/questions/58242768/using-pip-install-platform-to-install-so-on-windows

**workaround:**  
	gather dependencies for 'producerai' via Cloud9 and port them into the file system  

**any ideas?**
