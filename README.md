AWS Config: Monitoring Compliance for EC2 Instances
This project uses AWS Config to detect compliant and non-compliant EC2 instances based on the following rule:

Compliant EC2 Instance: Monitoring is enabled.
Non-Compliant EC2 Instance: Monitoring is not enabled.
Step 1: Set Up AWS Config
Log in to your AWS Management Console.

Navigate to the AWS Config service.

If you are using AWS Config for the first time, click on "Get started".

Configure the delivery channel settings, including specifying an Amazon S3 bucket where AWS Config will store configuration history.

Choose the resource types you want AWS Config to monitor. For this project, select "Amazon EC2 Instances".

Step 2: Create a Custom Config Rule
Navigate to the AWS Config console.

In the left navigation pane, click on "Rules".

Click on the "Add rule" button.

Choose "Create a custom rule".

Provide a name and description for your rule (e.g., "Monitoring Compliance for EC2 Instances").

Under "Scope of changes", select "Resources".

Define the rule trigger. Use AWS Lambda as the trigger source. If you haven't already, create a Lambda function that checks whether monitoring is enabled for an EC2 instance. The function will return the compliance status based on the monitoring configuration.

Step 3: Define the Custom Rule in AWS Config
Select your Lambda function from the dropdown list as the evaluator for the rule.

Specify the trigger type (e.g., "Configuration changes").

Save the rule.

Step 4: Monitor and Alert
AWS Config will continuously evaluate your EC2 instances against the rule you've created.

If any EC2 instance is found without monitoring enabled, the custom rule's Lambda function will mark it as non-compliant.
