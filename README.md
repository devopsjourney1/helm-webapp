
# Create the helmchart
helm create webapp1


# Install the first one
helm install mywebapp-release mywebapp/ --values mywebapp/values.yaml


# Upgrade after templating
helm upgrade mywebapp-release mywebapp/ --values mywebapp/values.yaml


# Accessing it
minikube tunnel


# Create dev/prod
k create namespace dev
k create namespace prod
helm install mywebapp-release-dev mywebapp/ --values mywebapp/values.yaml -f mywebapp/values-dev.yaml -n dev
helm install mywebapp-release-prod mywebapp/ --values mywebapp/values.yaml -f mywebapp/values-prod.yaml -n prod
helm ls --all-namespaces