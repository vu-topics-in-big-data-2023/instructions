# AWS Academy Learner Lab – Associate Services Restrictions
For purposes of your use of the Academy Learner Lab feature, the following restrictions apply. Region restriction
All service access is limited to the us-east-1 and us-west-2 Regions. If you load a service  console page in another AWS Region you will see access error messages.
Service usage and other restrictions
The following services can be used. Specific limitations apply as documented. Services  restrictions are subject to change.
- AWS Amplify
- Amazon API Gateway
- AWS App Mesh
- Application Auto Scaling
- AWS AppSync
- Amazon Athena
- Amazon Aurora
- AWS Backup
- AWS Batch
- AWS Budgets
- AWS Certificate Manager (ACM)
- AWS Cloud9
    - Supported Instance types: nano, micro, small, and medium.
- Amazon CloudFormation
- Amazon CloudFront
- Amazon CloudSearch
- AWS CloudShell
- AWS CloudTrail
- Amazon CloudWatch
- AWS CodeCommit
- AWS CodeDeploy
- AWS CodePipeline
- AWS CodeStar
- Amazon Cognito
- Amazon Comprehend
- AWS Config
- AWS Cost and Usage Report
- AWS Cost Explorer
- AWS Data Pipeline
- AWS Database Migration Service (AWS DMS)
- AWS DeepComposer
- AWS DeepLens
- AWS DeepRacer
- Amazon DynamoDB
- Amazon EC2 Auto Scaling
    - Supported Instance types: nano, micro, small, medium, and large.
    - Maximum of 32 vCPU used by concurrently running instances in an AWS  Region. For example, t2.micro instances use 1 vCPU each, so you could run up to  32 of them. However, t3.large instances use 2 vCPUs each, so you can run up to  16 of them. You can run a mix of instance types as long as you do not exceed the  32 vCPU threshold. Note that you are also limited to launching no more than nine  (9) instances (of any size) in a Region at once. Recommendation: size to your  actual need to avoid using up your cost budget.
- AWS Elastic Beanstalk
    - Supported Instance types: nano, micro, small, medium, and large. If you attempt  to launch a larger instance type, it will be terminated.
    - When you first create an environment in the console, it will use the default  security settings. However after the environment has been created, you may want  to edit the configuration's security settings. Change the service role to LabRole.  Similarly, set the IAM instance profile to LabInstanceProfile. If the environment  is in the us-east-1 AWS Region, you could set the EC2 key pair to vockey. These  settings will give you more permissions than the defaults.
- Amazon Elastic Block Store (EBS)
    - Maximum volume size is 100GB
    - PIOPs not supported
- Amazon Elastic Compute Cloud (EC2)
    - AMIs - Amazon provided Linux and Windows AMIs only.
    - Supported Instance types - nano, micro, small, medium, and large.
    - Instance quantity - Maximum of 32 vCPU used by concurrently running instances  in an AWS Region. For example, t2.micro instances use 1 vCPU each, so you  could run up to 32 of them. However, t3.large instances use 2 vCPUs each, so you  can run up to 16 of them. You can run a mix of instance types as long as you do  not exceed the 32 vCPU threshold. Note that you are also limited to launching no  more than nine (9) instances (of any size) in a Region at once. Recommendation:  size to your actual need to avoid using up your cost budget.
    - On-Demand instances only
    - EBS volumes - sizes up to 100 GB and type must be General Purpose SSD (gp2,  gp3 ) cold HDD (sc1), or standard.
    - Key pairs - If you are creating an EC2 instance in any AWS Region other than us east-1, the vockey key pair will not be available. In such cases, you should create  a new key pair and download it when creating the EC2 instance. Then use the new  key pair to connect to that instance.
    - A role named LabRole and an instance profile named LabInstanceProfile have  been pre-created for you. You can attach the role (via the instance profile) to an  EC2 instance when you want to access an EC2 instance (terminal in the browser)
    using AWS Systems Manager Session Manager. The role also grants permissions  to any applications running on the instance to access many other AWS services  from the instance.
    - Tip: to preserve your lab budget, stop any running EC2 instances before you are  done using the account for the day (or terminate them if not longer needed). When  your session ends, the lab environment may place any running instances into a  'stopped' state. Keep this in mind when you start a new session, that you may need  to start the stopped instance(s). Also, instances that have been stopped and started  again, will be assigned a new IPv4 public IP address unless you have an elastic IP  address associated with the instance.
- Amazon Elastic Container Registry (ECR)
- Amazon Elastic Container Service (ECS)
    - Supported Instance types: nano, micro, small, medium, and large.
- Amazon Elastic File System (EFS)
- Amazon Elastic Inference
- Amazon Elastic Kubernetes Service (EKS)
    - Supported Instance types: nano, micro, small, medium, and large.
- Elastic Load Balancing (ELB)
- Amazon Elastic MapReduce (EMR)
    - Supported Instance types: nano, micro, small, medium, and large. If you attempt  to launch a larger instance type, it will be terminated.
    - Maximum of 32 vCPU used by concurrently running EC2 instances in an AWS  Region.
- Amazon ElastiCache
- Amazon EventBridge
- AWS Fargate
- Amazon Forecast
- AWS Glue
- AWS Glue DataBrew
- Amazon GuardDuty
- AWS Health
- AWS Identity and Access Management (IAM)
    - Extremely limited access. You cannot create users or groups. You cannot create  roles, except that you can create service-linked roles.
    - Service role creation is generally permitted. If the service needs to create a role  for you, you may need to retry role creation if it fails the first time.
    - A role named LabRole has been pre-created for you. This role is designed to be  used when you want to attach a role to a resource in an AWS service. It grants  many AWS services access to other AWS services and has permissions very  similar to the permissions you have as a user in the console.
    - Example use: attach the LabRole via the instance profile named
    LabInstanceProfile to an EC2 instance for terminal in the browser access  to an EC2 instance guest OS using AWS Systems Manager Session
    Manager.
    - Another example: Attach the LabRole to a Lambda function so that the  Lambda function can access an S3, CloudWatch, RDS, or some other
    service.
    - Another example: Attach the LabRole to a SageMaker notebook instance  so that the instance can access files in an S3 bucket.
- AWS IAM Access Analyzer
- Amazon EC2 Image Builder
- Amazon Inspector
- AWS IoT 1-Click
- AWS IoT Analytics
- AWS IoT Core
- AWS IoT Greengrass
- Amazon Kendra
- AWS Key Management Service (KMS)
- Amazon Kinesis
- Amazon Kinesis Video Streams
- AWS Lambda
    o Tip: Attach the existing LabRole to any function that you create if that function  will need permissions to interact with other AWS services.
- Amazon Lex
- Amazon Lightsail
    - If you choose vCPU and memory specs that are too high (such as as 8 vCPU and  32GB) the instance may be terminated. Smaller sizes are supported.
- Amazon Machine Learning (Amazon ML)
- AWS Marketplace Subscriptions
    - Extremely limited read-only access.
- AWS Mobile Hub
- Amazon Neptune
- AWS OpsWorks
- Amazon Personalize
- Amazon Polly
- Amazon QuickSight
- Amazon Redshift
- Amazon Rekognition
- Amazon Relational Database Service (RDS)
    - Supported instance types: nano, micro, small, and medium.
    - Supported database engines: Amazon Aurora, MySQL, PostgreSQL and  MariaDB.
    - EBS volumes - size up to 100 GB and type General Purpose SSD (gp2). o On-Demand DB instance class types only
    - Multi-AZ deployments are not supported (choose Dev/Test or Free tier template if  prompted and do not create a standby instance).
    - Enhanced monitoring is not supported (you must uncheck this default setting). o Tip: to preserve your lab budget, stop any running RDS instances before you are  done using the account for the day (or terminate them if not longer needed). Be
    aware that if you do stop an RDS instance and leave it stopped for seven days,  AWS will start it again automatically, which will increase the cost impact. ∙ AWS Resource Groups & Tag Editor
- AWS RoboMaker
    - Supported Instance types for development environments: nano, micro, small,  medium, large, and c4.xlarge only.
- Amazon Route 53
    - You cannot register a domain
- Amazon SageMaker
    o Supported instance types: medium, large, and xlarge only.
- AWS Secrets Manager
- AWS Security Hub
- AWS Security Token Service (STS)
- AWS Serverless Application Repository (SAR)
- AWS Service Catalog
- Amazon Simple Notification Service (SNS)
- Amazon Simple Queue Service (SQS)
- Amazon Simple Storage Service (S3)
- Amazon Simple Storage Service Glacier (S3 Glacier)
    o You cannot create a vault lock
- Amazon Simple Workflow Service (SWF)
- AWS Step Functions
- AWS Storage Gateway
- Amazon Sumerian
- AWS Systems Manager (SSM)
    o A role named LabRole and an instance profile named LabInstanceProfile have  been pre-created for you. You can attach the role (via the instance profile) to an  EC2 instance when you want to access an EC2 instance (terminal in the browser)  using AWS Systems Manager Session Manager.
- Amazon Textract
- Amazon Timestream
- Amazon Transcribe
- Amazon Translate
- AWS Trusted Advisor
- Amazon Virtual Private Cloud (Amazon VPC)
- AWS WAF - Web Application Firewall
- AWS Well-Architected Tool
- AWS X-Ray
© 2021, Amazon Web Services, Inc., or its affiliates. All rights reserved.

# AWS Academy FAQ
[Official AWS academy FAQ](https://aws.amazon.com/training/awsacademy/faq/)
