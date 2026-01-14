minikube start    --- start the cluster 

<!-- 1. prepare the service and deployment file -->
<!-- 2. apply deployemnt and service  -->
kubectl apply -f file_service
kubectl apply -f file_deployment 
<!-- 3.get log of pods  -->
kubectl logs pods_id        after getting list of pods by :> kubectl get pod/deployemnt/service/etc
<!-- 4.get description of instances  -->
kubectl describe pod/deployment pods_id        after getting list of pods by :> kubectl get pod/deployemnt/service/etc
<!-- 5.delete instances -->
kubectl delete pod/deployment/service/etc inst_id    after getting list of pods by :> kubectl get pod/deployemnt/service/etc

