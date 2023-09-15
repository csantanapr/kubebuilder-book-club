# For pulling image from registry
make docker-build docker-push IMG=csantanapr/cronjobcontroller:v1.0.0
make install deploy IMG=csantanapr/cronjobcontroller:v1.0.0
make undeploy

# For local dev on kind
make docker-build IMG=csantanapr/cronjobcontroller:local
kind load docker-image cronjobcontroller:local --name kind
make install deploy IMG=csantanapr/cronjobcontroller:local

# For Monitoring
helm upgrade --install --wait --timeout 15m \
  --namespace kubebuilder-book-club-system \
  --create-namespace \
  --repo https://prometheus-community.github.io/helm-charts \
  kube-prometheus-stack kube-prometheus-stack \
  -f values.yaml

kubectl port-forward -n kubebuilder-book-club-system svc/kube-prometheus-stack-prometheus 8080:9090