# Lambda 101

The start of serverless technology, introduced at Reinvent 2014.   

Platform as a Service -- Amazon Elastic Beanstalk; you just have to update your code and let Amazon analyze your needs for you

Containers -- Isolated, lightweight, but you still have to deploy them to a server and have to keep the servers running

Serverless -- Don't have to worry about managing containers. Update your code and configure an event trigger.


## What is Lambda
Lambda encapsulates
- Data centers
- Hardware
- Assembly Code/Protocols
- High Level Languages
- Operating Systems
- Application Layer/AWS APIs

"AWS Lambda takes care of privisioning and managing the servers that you use to run your code, without worrying about operating systems, patching, scaling, etc"   
- Run as an event-driven compute service where events are changes an S3 bucket or an Amazon DynamoDB table
- Or it runs as a compute service in response to HTTP requests using the Amazon API gateway

### What is good about Lambda
- Lambda events can trigger other Lambda events, or other AWS servcies, which can themselves trigger other Lambda events
- Each instance of using Lambda is just one instance of Lambda instance running, so multiple users
- The nice thing is that it scales *up* and scales *out* effectively.
  - Scaling up increases the amount of resources in something (e.g., 4G -> 8G of RAM)
  - Scaling out adds new instances
- Each function can be hit by as many users as is necessary - even a simple function will be immediately deployed to as many users as hit the function
  - All iterations of a Lambda function, and routed using the right Availability Zones, etc

### What types of event triggers are there?
Event triggers are important to the exam.
- Some triggers are only available in certain regions (N. Virginia always gets them all)
- Core triggers (there are others): 
  - API Gateway 
    - A user's HTTP request goes to API gateway, and that triggers a Lambda function
    - If multiple users send to API gateway, each user's request invokes another Lambda function (one set of code responds to multiple requests)
  - Alexa Skills Kit 
    - every time you trigger Alexa, it's this trigger
  - CloudFront
  - CloudWatch 
  - DynamoDB
  - Kinesis
  - S3
  - SNS

## Creating a Lambda function
Author from scratch
- For the runtime environment, you can chose a range of languages, including Go, Python, C#, Java, Node.js
- Policy templates - using Simple Microservice permissions, which just allows execution of a Lambda function
- Then go in and configure your triggers (see section above)

### How is lambda priced?
- Number of requests -- first 1 million requests are free, $0.20 per 1 million thereafter
- Duration -- from the time your code begins executing until it returns or otherwise terminates, rounded up to the nearest 100ms. Price depends on the amount of memory you allocate to your function
  - LIMITED TO ONLY FIVE MINUTES OF FUNCTION TIME

### Why is it cool?
- No servers
- Continuous scaling, instantly
- Super super super cheap

### Practical use case
- Every time you speak to Alexa, you're talking to lambda

## Lambda Exam tips
- Lambda scales out (not up) automatically
- Lambda functions are independent, 1 event = 1 function
- Lambda is serverless
- Know what services are serverless!
- Lambda functions can trigger other lambda functions, 1 event can = x functions if functions trigger other functions
- Architectures can get extremely complicated, AWS X-ray can help debug
- Lambda can do things globally, you can use it to back up S3 buckets to other S3 buckets etc
- Know yr triggers
- Duration time is a maximum of five minutes
- Remember the languages available.

---
# Building a serverless website
This site will use Route53, API Gateway and Lambda
- Have to check that a domainname and bucketname are both available (check S3 bucket because it's free to register a bucketname)
  - Name both the same thing (e.g., helpmestudyawspolly.com; save bucket as helpmestudyawspolly)
  - Click over to properties on the S3 bucket and Properites -> Enable Static Website
  - Add "index.html" and "error.html" to the S3 bucket
- Then add 
- Make sure to note the region that your Lambda function is in, because that is where it will be saved when you go to set up the Lambda integration when setting up the Serverless Website in the API Gateway

### BDA serverless website
- Mad libs. Leave a few nouns and adjectives open to fill in.
- The Lambda function will then be a Google API call that ranks the sentiment
