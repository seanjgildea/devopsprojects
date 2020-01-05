# Terraform with Docker, ECR and AWS

- [Requires IAM User w/ Admin rights via an Access Key and Secret Key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey)
- [Requires AWS CLI on command line](https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html)

## Docker and ECR

```
  aws ecr get-login
```

- Use the output to log into AWS Repository
- Next build the docker image but make sure to tag it with the ECR repo

```
  docker build -t xxxxxxxxxxxxx.dkr.ecr.us-east-1.amazonaws.com/myapp:1
```

- From the directory you built your image, run the following command to push the docker image to ECR

```
  docker push xxxxxxxxxxx.dkr.ecr.us-east-1.amazonaws.com/myapp
  
```
- Login to the AWS Console and go to ECR .... or type the following command 

```
  aws ecr describe-repositories
```

## ECS

- 


