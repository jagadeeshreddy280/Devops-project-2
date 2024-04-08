# Devops-project-2

![Eks-ci_cd](https://github.com/jagadeeshreddy280/Devops-project-2/assets/116871383/c1b96445-284a-4938-bfd2-c431c1c5d710)


Deploy an Application on EKS using CI/CD
---

pre-requisite:-
---
cloud platform : AWS(IAM,EKS,VPC)

SCM : Github

CI/CD : Jenkins

Container platform : DockerHub

Infrastructure : Terraform

Step 1:
Terraform Installation:
---
```
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```
```
sudo apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
```
```
sudo apt update
```
```
sudo apt install terraform
```
AWS cli
---
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
```
unzip awscliv2.zip
```
```
sudo ./aws/install --update
```
kubectl 
---
```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
```
```
chmod +x ./kubectl
```
```
sudo mv ./kubectl /usr/local/bin/kubectl
```
```
kubectl version
```
```
aws eks update-kubeconfig --region us-east-1 --name EKScluster
```

o/p:
    Client Version: v1.29.1

    Kustomize Version: v5.0.4-0.20230601165947-6ce0bf390ce3
    
    Server Version: v1.29.0-eks-c417bb3

Step 2:    
jenkins installation:
---
ubuntu ec2: https://pkg.jenkins.io/debian-stable/

linux ec2: https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/

java Need to Install:
---
sudo apt-get update

sudo apt install openjdk-11-jdk

java --version

sudo mkdir jenkins

sudo chmod 777 -R jenkins

Step 3:
opening jenkins web
---
localhost:8080

Step 5:
---
Install jenkins,Docker,git

Docker 
```
sudo apt install docker.io
```
Enableing the docker on ec2
```
sudo systemctl enable docker
```
Starting the docker on ec2
```
sudo systemctl start docker
```
Checking the status of docker 
```
sudo systemctl status docker
```
Checking the status of jenkins
```
sudo systemctl status jenkins
```
```
sudo apt-get update
```
Need to install java latest version
```
sudo apt install openjdk-11-jdk
```
```
java --version
```
<img width="615" alt="Screenshot 2024-04-05 113946" src="https://github.com/jagadeeshreddy280/Devops-project-1/assets/116871383/20d144be-a017-4463-90f2-3d0f5f7de128">


Grant permission for docker 
```
sudo chmod 666 /var/run/docker.sock
```

copy publicip:8080 on browser 
```
  username: admin
  
  password: cat /var/lib/jenkins/secrets/initialAdminPassword
```
![image](https://github.com/jagadeeshreddy280/Devops-project-1/assets/116871383/147aac4f-57af-4246-aeea-9ee087e03a47)

Add Cred in jenkins:
---
1.Go to settings-->developer settings-->token-->new token (tick all boxes) -->create
 
2.Copy token use as password
Jenkins: ghp_Lmxn7epc

<img width="934" alt="Screenshot 2024-04-05 140534" src="https://github.com/jagadeeshreddy280/Devops-project-1/assets/116871383/3db5cc4e-ad9a-425b-b162-d6fa6ff4b577">


3.Save Git & Docker & nomad token in Jenkins

4.Go to Manage jenkins --> click Manage Credentials --> click system

![image](https://github.com/jagadeeshreddy280/Devops-project-1/assets/116871383/4ca28177-15e9-4b38-9426-8cc93e16f1c8)


5.Go to Global credentials (unrestricted) --> Add cred

![image](https://github.com/jagadeeshreddy280/Devops-project-1/assets/116871383/318641d8-06e8-483d-8cc4-7641054dfb01)

Step 4:
Trigger jenkins job automatically whenever any changes in GitHub:-
---
IN GITHUB:

Go to repository

Inside repo --> settings -->click webhooks -->click add webhooks

Copy Jenkins url like http://2.33.344.44:8080 and Add /github-webhook/

Example: http://35.154.114.196:8080/github-webhook/

Add in Payload URL --> save it.

Change anything or push any file into git repo we can see job is triggered automatically.

NOTE: Save Git & Docker  in Jenkins

Go to Manage Jenkins --> Credentials --> Add New Credentials ** Need to connect Github to jenkins:

Go to settings-->developer settings-->token-->new token (tick all boxes) -->create

Copy token use as password Jenkins: ghp_Lmxn7epc


OnlineBookStore Application :
---
https://github.com/jagadeeshreddy280/onlinebookstore.git

Check Application pods & service are Running
```
kubectl get all -n app
```
```
   NAME                                     READY   STATUS    RESTARTS   AGE
   adservice-76bdd69666-ckc5j               1/1     Running   0          2m58s
   cartservice-66d497c6b7-dp5jr             1/1     Running   0          2m59s
   checkoutservice-666c784bd6-4jd22         1/1     Running   0          3m1s
   currencyservice-5d5d496984-4jmd7         1/1     Running   0          2m59s
   emailservice-667457d9d6-75jcq            1/1     Running   0          3m2s
   frontend-6b8d69b9fb-wjqdg                1/1     Running   0          3m1s
   loadgenerator-665b5cd444-gwqdq           1/1     Running   0          3m
   paymentservice-68596d6dd6-bf6bv          1/1     Running   0          3m
   productcatalogservice-557d474574-888kr   1/1     Running   0          3m
   recommendationservice-69c56b74d4-7z8r5   1/1     Running   0          3m1s
   redis-cart-5f59546cdd-5jnqf              1/1     Running   0          2m58s
   shippingservice-6ccc89f8fd-v686r         1/1     Running   0          2m58s
   ```
Edit frontend-6b8d69b9fb-wjqdg Service from Nodeport to LoadBalancer
 ```
kubectl edit svc frontend-6b8d69b9fb-wjqdg -n app
```
Change to LoadBalancer

copy service url in google u can access it.
![image](https://github.com/jagadeeshreddy280/Observability-setup/assets/116871383/457685e9-b172-4806-8f8e-aa79fb785c01)





Any Queries related
---
Gmail : jagadeeshbhavanam@gmail.com
---
linkedin : https://www.linkedin.com/in/bhavanam-jagadeeswara-reddy-1b85801b6
---
