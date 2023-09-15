# For pulling image from registry
make docker-build docker-push IMG=csantanapr/cronjobcontroller:v1.0.0
make install deploy IMG=csantanapr/cronjobcontroller:v1.0.0
make undeploy

# For local dev on kind
make docker-build IMG=csantanapr/cronjobcontroller:local
kind load docker-image cronjobcontroller:local --name kind
make install deploy IMG=csantanapr/cronjobcontroller:local
