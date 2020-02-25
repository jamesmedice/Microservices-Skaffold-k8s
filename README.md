First step : run install.sh

gcloud container clusters create $_CLUSTER --zone $_ZONE

gcloud container clusters get-credentials $_CLUSTER --zone $_ZONE


skaffold:
curl -Lo skaffold https://storage.googleapis.com/skaffold/releases/v0.36.0/skaffold-linux-amd64 && chmod +x skaffold && sudo mv skaffold /usr/local/bin


skaffold run