# Hands-on Demo #
<p>The system appears to be very slow. We identify the problem and find that the traffic between staff-service and driver-monitoring service takes too much time. To improve on performance we take the problematic one out of the picture so we set up a timeout so that the rest of the application can work on.</p>

cd warmup-excercise
## Apply istio and kiali ##
kubectl apply -f .\1-istio-init.yaml

kubectl apply -f .\2-istio-minikube.yaml

kubectl apply -f .\3-kiali-secret.yaml
## Label your namespace ##
kubectl label ns default istio-injection=enabled

kubectl describe ns default
## Apply your application ##
kubectl apply -f .\4-application-full-stack.yaml

## Check the pods/svcs running in the namespace ##
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