Steps to deploy Jenkins(with BlueOcean and Docker features) on Kubernetes cluster

Step 1 - Create Namespace for Jenkins in Kubernetes 
-> kubectl create namespace kv-devops-tools

Step 2 - Create Kubernetes Persistent Volume for storing persistent data/config
Note: Portainer on TrueNas Scale is NOT showing Kube Volumes on Portrainer UI. Use kubectl for managing PV related things.
-> kubectl apply -f jenkins-pv.yaml

Step 3 - Create Kubernetes PVC
-> kubectl apply -f jenkins-pvc.yaml

Step 4 - Run Kubernetes Deployment and Services jobs
Note: jenkins yaml file contains both deployment and service configuration.
-> kubectl apply -f jenkins.yaml

Initial Jenkins Configuration
1. Add Maven Tool in Jenkins Global Tools.
2. Add DockerHud Creds in Jenkins Global Credentials for pushing Docker images.
3. Configure JDK with Private CA as Trusted Authorities... i.e. update cacerts in jdk