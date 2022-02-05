# K8S Helm Introduction

The content in this repository is based on the
[Introduction to Helm | Kubernetes Tutorial | Beginners Guide](https://youtu.be/5_J7RWLLVeQ)
video.

```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64
chmod +x ./kind
sudo mv kind /usr/local/bin
kind create cluster
kind create cluster --image kindest/node:v1.23.3
docker run -it --rm -v ${HOME}:/root -v ${PWD}:/work -w /work --net host alpine sh
```

In the shell create by the last command do the following.

```sh
apk add --no-cache curl
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
mv ./kubectl /usr/local/bin/kubectl
export KUBE_EDITOR="vi"
# from https://github.com/helm/helm/releases
curl -LO https://get.helm.sh/helm-v3.8.0-linux-amd64.tar.gz
tar -C /tmp/ -zxvf helm-v3.8.0-linux-amd64.tar.gz
rm helm-v3.8.0-linux-amd64.tar.gz
mv /tmp/linux-amd64/helm /usr/local/bin/helm
chmod +x /usr/local/bin/helm
helm create example app
```

After creating the above directory did the following:

- Removed all yaml files from the temp
- put in template directory yaml from
  - https://github.com/carltonj2000/k8s-crs-1

Decided to do the rest for outside the above container.

```
helm template example-app example-app
helm install example-app example-app
helm upgrade example-app example-app --values ./example-app/values.yaml
kubectl --namespace default port-forward webapp-deployment-56dbf5d695-k242m 8080:3000
```
