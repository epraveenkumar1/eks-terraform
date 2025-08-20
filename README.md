# EKS-Terraform

## Install AWS CLI
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install unzip curl -y
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

## Install Terraform
**Clone the git repository**
```bash
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```
**Initialise terraform and automate**
```bash
terrafrom init
terraform plan
terraform apply --auto-approve
terraform destory --auto-approve
```

## Kubeconfig
**Connect to the eks cluster**
```bash
aws eks --region ap-south-1 update-kubeconfig --name -devopsshack-cluster
```

## Install Kubectl
**Kubectl is used to communicate withe the cluster**
```bash
# 1. Download the latest release
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
# 2. Make the binary executable
chmod +x kubectl
# 3. Move the binary to a directory in your PATH
sudo mv kubectl /usr/local/bin/
# 4. Verify the installation
kubectl version --client
```
```bash
# Befor this command, connect to the cluster created
kubectl get nodes
```

