# Simple_Kubernets_cluster_with_KIND
===============

**Step1: Install kubectl**
-----------
refer KB: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/


- Download the latest release with the command:

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

- Download the kubectl checksum file:

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"

- Validate the kubectl binary against the checksum file (output should be "kubectl: OK") :

echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check


- Install kubectl

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

kubectl version --client


**Step2: KIND installation**
----------
refer KB: https://kind.sigs.k8s.io/docs/user/quick-start/#installation
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.27.0/kind-linux-amd64

chmod +x ./kind

sudo mv ./kind /usr/local/bin/kind

kind version

**Step3: Install docker**
------------

sudo apt-get update
sudo install docker.io


**To create kind cluster**

kind create cluster --name=my-cluster --config=config.yaml

kubectl cluster-info --context kind-my-cluster        // view the cluster information

kubectl get nodes          //  List the nodes under the cluster


kind delete cluster        // delete kind cluster
