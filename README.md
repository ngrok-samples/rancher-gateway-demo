# rancher-gateway-demo
Demo of using the Gateway API in the ngrok Kubernetes Operator with Rancher in AWS and DigitalOcean

# SUSECON 24 Demo
## Configuring ngrok Kubernetes Operater in Rancher
### Install ngrok Helm Chart

Add ngrok repo to helm.
```bash
helm repo add ngrok https://ngrok.github.io/kubernetes-ingress-controller
```

Install the Gateway CRDs in order to use the Gateway objects
```bash
kubectl apply -f https://github.com/kubernetes-sigs/gateway-api/releases/download/v1.0.0/standard-install.yaml
```

Install ngrok Kubernetes Operator helm chart
```bash
helm install ngrok-ingress-controller ngrok/kubernetes-ingress-controller \
  --namespace ngrok-ingress-controller \
  --create-namespace \
  --set credentials.apiKey=$NGROK_API_KEY \
  --set credentials.authtoken=$NGROK_AUTHTOKEN \
  --set useExperimentalGatewayApi=true  # gateway preview