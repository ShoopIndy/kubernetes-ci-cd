minikube start --memory 8000 --cpus 2 --kubernetes-version v1.6.0

kubectl apply -f manifests/jenkins.yml

kubectl rollout status deployment/jenkins

kubectl exec -it `kubectl get pods --selector=app=jenkins --output=jsonpath={.items..metadata.name}` cat /root/.jenkins/secrets/initialAdminPassword

