# For pulling image from registry
make docker-build docker-push IMG=csantanapr/cronjobcontroller:v1.0.0
make deploy IMG=csantanapr/cronjobcontroller:v1.0.0
make undeploy

# For local dev on kind
make docker-build docker-push IMG=csantanapr/cronjobcontroller:local
docker images
kind load docker-image cronjobcontroller:local --name kind
make deploy IMG=csantanapr/cronjobcontroller:local
