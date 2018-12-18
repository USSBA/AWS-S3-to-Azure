# AWS-S3-to-Azure
This Node.js code is used to take objects written to AWS S3 bucket and push the object's content to a SNS topic. SNS topic points to an Azure Logic App HTTPS trigger.

On the AWS side I modified AWS Lambda tutorial code (https://docs.aws.amazon.com/lambda/latest/dg/with-cloudtrail-example.html) to work for our use case. Created a new Lambda function, called ‘s3toAzureHTTPTrigger’ and uploaded the code and supporting libraries. Created an SNS topic, ‘SOCLogs’, and added an HTTPS subscription that points to an Azure endpoint. From their configured the specified bucket to send all event creation notifications to the ‘s3toAzureHTTPTrigger’ Lambda. 

On the Azure Side, created a Logic App configured to listen to a HTTPS endpoint. Once triggered the logic app parses the JSON received then pushes it to the Log Analytics Pool. 

Note: Be sure to install Node on your machine and install async (https://github.com/caolan/async).
