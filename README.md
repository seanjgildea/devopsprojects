# A collection of DevOps for 2020 

- [Spring Boot with Dockerfile and external properties](spring-boot-dockerfile.md)

- [Terraform, Docker, ECR and AWS](terraform_docker_ecr_aws.md)

- Spring Cloud Kubernetes app using AP4K for YAML generation for Kubernetes
  - kubectl create --filename target/classes/META-INF/ap4k/kubernetes.yml
  - Chaos-monkey integration
  - Swagger API
  - Kubernetic to monitor the pods/deployment/config
  - GatewayApplication.java w/ RouteLocator containing load balanced URI endpoints containing service names
  - https://www.youtube.com/watch?v=u64jexEX_RY

## Docker with Java

- In Stage 1, Use a JDK to build the image and in Stage 2, use the JAR + a JRE as a base image. Save bloat. 
- Use docker-compose.dev.yml or docker-compose.prod.yml names for different environments
- Use docker --memory to set a limit for the container
- Use docker stats to monitor resources in your container

## K8's

- For kubernetes, you typically do not need the ssh key. You use kubernetes commands to get a shell within a pod
- kubectl get pods
- kubectl exec -it pod sh
- kubectl config set-context --current --namespace=dev-ep6
- kubectl get namespace
- kubectx to switch namespaces
