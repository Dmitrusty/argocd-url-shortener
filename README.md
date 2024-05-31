# argocd-url-shortener
Test ArgoCD url-shortener project

### Инсталляция ArgoCD:
в папке:
~/Documents/Work/Projects/Kubernetes for office/minikube deployments/ArgoCD/  
```
kubectl create namespace argocd  
kubectl apply -n argocd -f install.yaml
```
### ПОДКЛЮЧЕНИЕ к UI ArgoCD:
пробросим порт:  
`kubectl port-forward -n argocd svc/argocd-server 8080:443`  

creds:          admin  
password:       the field password in a secret named `argocd-initial-admin-secret`
in your Argo CD installation namespace

to retrieve this password:  
```
kubectl get secrets argocd-initial-admin-secret -n argocd -o yaml
echo bHBxQkgwb1hsNUo1b3EtYQ== | base64 -d
```
### ЗАПУСК CD проекта ArgoCD:
корень проекта:  
~/Documents/Work/Projects/Learning/Kubernetes-main/012 ArgoCD/ArgoCD
```
kubectl apply -f argo-app.yaml
```
### ОСТАНОВ CD проекта ArgoCD:
```
kubectl delete -f argo-app.yaml
```
### РУЧНОЙ АНДЕПЛОЙ ПРИЛОЖЕНИЯ - указывать неймспейс явно:
папка манифеста приложения:  
~/Documents/Work/Projects/Learning/Kubernetes-main/012 ArgoCD/ArgoCD/dev  
```
kubectl -n url-shortener delete -f url-shortener.yaml
kubectl delete namespace url-shortener
```
### деинсталляция ArgoCD:
в папке:  
~/Documents/Work/Projects/Kubernetes for office/minikube deployments/ArgoCD/
```
kubectl delete -n argocd -f install.yaml
kubectl delete namespace argocd
```