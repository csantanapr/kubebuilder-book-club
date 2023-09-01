make docker-build docker-push IMG=csantanapr/cronjobcontroller:v1.0.0
make deploy IMG=csantanapr/cronjobcontroller:v1.0.0
make undeploy


make docker-build IMG=cronjobcontroller:local
docker images
kind load docker-image cronjobcontroller:local --name kind
make deploy IMG=cronjobcontroller:local
