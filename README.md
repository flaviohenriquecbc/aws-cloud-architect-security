# AWS Cloud Architect Nanodegree: Design for Security

This is a project for the Udacity AWS Cloud Architect Nanodegree: Design for Security

# Project Overview: Cloud Security - Protecting Resources and Data in the Cloud
The scope of this project is:

- Deploy and assess a simple web application environment’s security posture
- Test the security of the environment by simulating attack scenarios and exploiting cloud configuration vulnerabilities
- Implement monitoring to identify insecure configurations and malicious activity
- Apply methods learned in the course to harden and secure the environment
- Design a DevSecOps pipeline


## Deploying the infra

### Deploy the S3 buckets:
```
aws cloudformation create-stack --region us-east-1 --stack-name c3-s3 --template-body file://provision/c3-s3.yml
```

### Deploy the VPC and Subnets:
```
aws cloudformation create-stack --region us-east-1 --stack-name c3-vpc --template-body file://provision/c3-vpc.yml
```

### Deploy the Application stack:
```
aws cloudformation create-stack --region us-east-1 --stack-name c3-app --template-body file://provision/c3-app.yml --parameters ParameterKey=KeyPair,ParameterValue=<add your key pair name here> --capabilities CAPABILITY_IAM
```

### Upload data to S3 buckets
```
aws s3 cp ./content/free_recipe.txt s3://<BucketNameRecipesFree>/ --region us-east-1
```

```
aws s3 cp ./content/secret_recipe.txt s3://<BucketNameRecipesSecret>/ --region us-east-1
```

At this moment, it should be possible to access your application at: `http://<ApplicationURL>/free_recipe`


