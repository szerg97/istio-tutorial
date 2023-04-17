# Telemetry #
cd 1-Telemetry

## Apply files ##
kubectl apply -f .\1-istio-init.yaml

kubectl apply -f .\2-istio-minikube.yaml

kubectl apply -f .\3-kiali-secret.yaml

kubectl apply -f .\4-label-default-namespace.yaml

kubectl apply -f .\5-application-no-istio.yaml
## Check pods ##
kubectl get pods

kubectl get pods -n istio-system

kubectl get svc

kubectl get svc -n istio-system
## Check the webapp in the browser
kubectl port-forward svc/fleetman-webapp 8080:80
## Check Kiali in the browser
kubectl port-forward svc/kiali 20001:20001 -n istio-system
## Check Jaeger in the browser
kubectl port-forward svc/tracing 30001:80 -n istio-system