# code_challenge

1) I followed this link to dockerize a ruby on rails app 
   link: https://semaphoreci.com/community/tutorials/dockerizing-a-ruby-on-rails-application

2) link to my github repo:
   https://github.com/AlaaAbdelkareem/Dockerizing-a-Ruby-on-Rails-Application.git

3) I translate the dockerfile and docker compose to kubernetes resources 
link to my github repo: https://github.com/AlaaAbdelkareem/RubyOnRails_with_kubernetes

steps:

1- start the cluster using minikube
   
   minikube start

2- create the secret to store postgres password and secret token

 kubectl create secret generic postgres-pass --from-literal=password=yourpassword
 
 kubectl create secret generic token --from-literal=password=asecuretokenwouldnormallygohere

 
3- create the Kube resources for postgres
 
 kubectl create -f postgres/postgres-persistentvolumeclaim.yaml 
 
 kubectl create -f postgres/postgres-service.yaml
 
 kubectl create -f postgres/postgres-deployment.yaml 


4- create the kube resources for redis
 
 kubectl create -f redis/redis-persistentvolumeclaim.yaml 
 
 kubectl create -f redis/redis-service.yaml
 
 kubectl create -f redis/redis-deployment.yaml 


5- create the kube resources for sidekiq
 
 kubectl create -f sidekiq/sidekiq-service.yaml 
 
 kubectl create -f sidekiq/sidekiq-deployment.yaml 


6- Kube Job
 
 kubectl create -f migrate.yaml


7- create app resources
 
 kubectl create -f drkiq/drkiq-service.yaml 
 
 kubectl create -f drkiq/drkiq-deployment.yaml 








