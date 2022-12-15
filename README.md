## Helm Chart for K8s Monitoring using Python script


# This Chart deploys python scripts as containers 1) webserver to server index.html generated by python script 2) python script collects metrics from metrics-server(/apis/metrics.k8s.io/v1beta1) and k8s api server (/api/v1) and generates index.html.

deployment.yaml deploys containers python-app and web-server with env variable TOKEN  and volumemount /web/html which shared between the containers in a POD. 

service.yaml exposes the container on specific port externally as loadbalancer service.

clusterrole.yaml creates clusterrole,clusterrolebinding  and serviceaccount with token secret which is used as env variable in python-app container, to provide access to resources and authenticate k8s apis and metrics server using apigroups.

components-2.yaml deploys metrics server in kube-system namespace.