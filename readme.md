# Hands-on Demo #
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

## Check the pods running in the namespace ##
kubectl get pods