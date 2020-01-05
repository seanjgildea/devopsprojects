# Terraform with Docker, ECR and AWS

- [Requires IAM User w/ Admin rights via an Access Key and Secret Key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey)
- [Requires AWS CLI on command line](https://docs.aws.amazon.com/cli/latest/userguide/install-macos.html)

```
  aws ecr get-login
```

- Use the output to log into AWS Repository
- Next build the docker image 
- From the directory you built your image, run the following command to push the docker image to ECR

```
  docker push xxxxxxxxxxx.dkr.ecr.us-east-1.amazonaws.com/myapp
  
```



