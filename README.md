STEPS: 

export _ZONE=us-central1-a
export _CLUSTER=gateway
export PROJECT=$DEVSHELL_PROJECT_ID

gcloud services enable container.googleapis.com 

gcloud services enable containerregistry.googleapis.com

gcloud auth configure-docker -q

gcloud container clusters create $_CLUSTER --zone $_ZONE

gcloud container clusters get-credentials $_CLUSTER --zone $_ZONE


skaffold:
curl -Lo skaffold https://storage.googleapis.com/skaffold/releases/v0.36.0/skaffold-linux-amd64 && chmod +x skaffold && sudo mv skaffold /usr/local/bin

skaffold run -p gcb --default-repo=gcr.io/$PROJECT_ID