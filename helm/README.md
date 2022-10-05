# Helm chart for APK

## Prerequisites

* Install [Helm](https://helm.sh/docs/intro/install/)
  and [Kubernetes client](https://kubernetes.io/docs/tasks/tools/install-kubectl/) <br><br>

* An already setup [Kubernetes cluster](https://kubernetes.io/docs/setup). If you want to run it on the local you can use Minikube or Kind or a similar software.<br><br>

* Install [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/deploy/). If you are using Minikube you can install ingress by running ```minikube addons enable ingress```<br><br>
    

## Steps to deploy APK DS servers and CloudNativePG

```HELM-HOME``` = APKCTL-demo/helm

1. Execute ``` helm repo add bitnami https://charts.bitnami.com/bitnami ```
2. Follow IPK's 'Install from a chart respository' guide here : https://docs.google.com/document/d/1GJxX7BiYL44mfnCJtm-JfiuwrMmIGC-DkQI5YZ_93zk
    <br>

    When following the IPK guide's "Add chart museum repo to helm" step, if you used 8080 port, change the port in ```HELM-HOME```/Chart.yaml ipk.repository value according to that. 

3. Clone the repo and cd into the ```HELM-HOME``` folder.
4. Execute ``` helm dependency build ``` command to download the dependent charts.
5. Now execute ```helm install apk-test . --set ipk.wso2.subscription.username=<username> --set ipk.wso2.subscription.password=<password>``` to install the APK components.
6. If you dont want to spin up postgres db : use ```  --set wso2.apk.cp.postgresql.enabled=false ``` in the helm install command
7. If you dont want to spin up IPK components : use ```   --set wso2.apk.cp.ipk.enabled=false ``` in the helm install command