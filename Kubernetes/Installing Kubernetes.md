
```toc
```

## Full Installation

### Prereqs
- Disable swap
- Enable overlay and br_netfilter kernel modules
- Enable IPv4 forwarding
- Set Netfilter conntrack max connections to 524288

````ad-example
title: shell commands
collapse: true
```bash
sed -i '/swap/d' /etc/fstab
swapoff -a

cat <<'EOT' >> /etc/modules-load.d/k8s.conf
overlay
br_netfilter
EOT

cat <<'EOT' >> /etc/sysctl.d/k8s.conf
net.ipv4.ip_forward = 1
net.netfilter.nf_conntrack_max = 524288
EOT

sysctl --system
```
````

### Install Container Runtime
- Configure docker.io repository or download software.
- Install `docker-ce`, `docker-ce-cli`, `containerd.io`, and `docker-compose-plugin`
- Rewrite `/etc/containerd/config.toml` with output from `containerd config default`
- Set `SystemdCgroup=true` in `/etc/containerd/config.toml`, section `[plugins.*io.containerd.grpc.v1.cri.*containerd.runtimes.runc.options]`
- Restart containerd
````ad-example
title: shell commands
collapse: true
```bash
# Install docker packages from docker.io repository - method varies by OS
key=$(mktemp)
ring=$(mktemp)
wget -O ${key} "https://download.docker.com/linux/debian/gpg"
gpg --no-default-keyring --keyring "${ring}" --import "${key}"
gpg --no-default-keyring --keyring "${ring}" --export --output "/etc/apt/keyrings/docker.gpg"
rm -f "${key}" "${ring}"

echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian bullseye stable" > /etc/apt/sources.list.d/docker.list

apt update
apt -y install docker-ce docker-ce-cli containerd.io docker-compose-plugin

containerd config default | sed -e '/\[plugins.*io.containerd.grpc.v1.cri.*containerd.runtimes.runc.options\]/,/^\s*\[/s/SystemdCgroup.*$/SystemdCgroup=true/g;' > /etc/containerd/config.toml

systemctl restart containerd
```
````

### Install Kubernetes Components
- This includes `kubeadm`, `kubectl`, and `kubelet`.
````ad-example
title: shell commands
collapse: true
```bash
# Install kubernetes packages from repository - method varies by OS
key=$(mktemp)
ring=$(mktemp)
wget -O ${key} "https://packages.cloud.google.com/apt/doc/apt-key.gpg"
gpg --no-default-keyring --keyring "${ring}" --import "${key}"
gpg --no-default-keyring --keyring "${ring}" --export --output "/etc/apt/keyrings/k8s.gpg"
rm -f "${key}" "${ring}"

echo "deb [signed-by=/etc/apt/keyrings/k8s.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" > /etc/apt/sources.list.d/k8s.list

apt update
apt -y install kubeadm kubectl kubelet
```
````

### Initialize the Cluster
- Initialize the cluster on the master node.
- Apply the 'flannel' network driver.
- Join each worker node to the cluster.
````ad-example
title: shell commands
collapse: true
**On the master node**
```bash
kubectl init --apiserver-advertise-address "public_ip"
export KUBECONFIG=/etc/kubernetes/admin.conf
kubectl apply -f https://raw.githubusercontent.com/flannel-io/flannel/master/Documentation/kube-flannel.yml
```
**On the worker nodes**, run the `kubeadm join` command given in the output of the `init` command.
````

## Minikube
This is a small testing scenario for learning or testing Kubernetes

### OSX
```
brew install hyperkit minikube
minikube start --vm-driver=hyperkit
```


----
# See Also
[Kubernetes on Debian 11](https://www.natarajmb.com/2022/06/kubernetes-debian/)
[Installing kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
[Flannel (GitHub)](https://github.com/flannel-io/flannel#deploying-flannel-manually)
[Using kubeadm with multiple network interfaces - GitHub](https://github.com/kubernetes/kubernetes/issues/33618)
[kubeadm init](https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm-init/)

