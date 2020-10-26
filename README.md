# AWS_Rolling_Update
### Introduction
<img src="https://github.com/sumanth979/AWS_Rolling_Update/blob/main/rolling_update.gif" alt="Rolling Upgrade">

### AWS Resources Invloved:
* EC2 - Elastic Compute Cloud
* ASG - Auto Scaling Group
* ALB - Application Load Balancer
* SG - Secuirty Groups

- - - -
### Deployment Architecture Diagram
<img src="https://github.com/sumanth979/AWS_Rolling_Update/blob/main/architecture.png" alt="Architecture">

- - - -
### Input & Output Details:
#### Input
* The inputs for the deployment will be provided 
  * Trough UI if deployment is done using AWS UI.
  * Through **parameters.json** file if the deployment is done using AWS Console.

* The input variable **VersionParameter** specifies the app deployment version.

#### Output
* The Load Balancer DNS details.
<img src="https://github.com/sumanth979/AWS_Rolling_Update/blob/main/output.png" alt="Output">

- - - -
## Deploy using AWS Console
* To Create the stack details
```
aws cloudformation create-stack --stack-name stackName --template-body file://cf_deployment_template.yaml --role-arn roleARN --parameters file://parameters.json
```
* To describe the stack details (to get the details of stack)
```
aws cloudformation describe-stacks --stack-name stackName > stackDetails.json
```
* To Update the stack details
```
aws cloudformation update-stack --stack-name stackName --role-arn roleARN --parameters file://parameters.json --use-previous-template
```
* To Delete the stack details
```
aws cloudformation delete-stack --stack-name stackName
```

