kubectl create namespace ignite
kubectl create -f service.yaml
kubectl create sa ignite -n ignite
kubectl create -f cluster-role.yaml
kubectl create configmap ignite-config -n ignite --from-file=node-configuration.xml
kubectl create -f deployment.yaml
kubectl get pods -n ignite
kubectl logs ignite-cluster-5b69557db6-lcglw -n ignite
kubectl exec -it <pod_name> -n ignite -- /bin/bash
/opt/ignite/apache-ignite/bin/control.sh --set-state ACTIVE --yes
kubectl scale deployment ignite-cluster --replicas=3 -n ignite
