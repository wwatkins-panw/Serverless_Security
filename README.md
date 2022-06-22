# Serverless_Security
Serverless function used for testing security features of Prisma Cloud

Steps to deploy function and setup test events
- Open Prisma Cloude console with Sysadmin or Cloud Provisioning Admin Role
- Open AWS Management console with the AWSLambda_FullAccess permission

From AWS Console
- Create a blank Lambda Function in AWS
- Expand "Change default exection role" and select "Create new role from AWS template" and Basic Lambda@Edge permission
- Click Create Function

From Prisma Cloud
- Download twistloc defender from console.  (ZIP or Curl command)
Upload Twistloc layer to AWS
- Open Lambda->Layers to add new customer twistloc layer to AWS
- Create Layer, upload from zip, using zip downloaded from console
Change Handler
- Open Lambda->Functions->NEW FUNCTION CREATED, add layer, Customer Layer, select twistloc layer
- Open Code Tab-> Scroll down to Runtime section, copy the original handler, end then change to twistlock.handler
From Prisma, Create Twistloc policy key
Create two environment variables
-   ORIGINAL_HANDLER - with the value of the copied handler earlier
-   TW_POLICY - with the value of the key generated from the console
Create Test Events
- Create new event
- copy events from files
