# A collection of DevOps for 2020 

- [Spring Boot with Dockerfile and external properties](spring-boot-dockerfile.md)

- Spring Cloud Kubernetes app using AP4K for YAML generation for Kubernetes
  - kubectl create --filename target/classes/META-INF/ap4k/kubernetes.yml
  - Chaos-monkey integration
  - Swagger API
  - Kubernetic to monitor the pods/deployment/config
  - GatewayApplication.java w/ RouteLocator containing load balanced URI endpoints containing service names
  - https://www.youtube.com/watch?v=u64jexEX_RY

- Kubernetes secrets file being read by a Spring Boot container project

- Kubernetes cluster of microservices

- Lambda functions running in a Docker container deployed

- Lambda functions that hit Amazon MQ and DynamoDB backend

- Running a container on EC2

- Step Functions

- AWS Workflow

- NGinx reverse proxy with cnames


- For kubernetes, you typically do not need the ssh key. You use kubernetes commands to get a shell within a pod
- kubectl get pods
- kubectl exec -it pod sh
- kubectl config set-context --current --namespace=dev-ep6
- kubectl get namespace
- kubectx to switch namespaces
