## kubernetes-setup-on-Redhat7_64

# Steps to be followed for setting up the kubernetes Cluster Setup in Control Plane mode


1  sudo visudo
2  exit

3  yum upgrade

4  subscription-manager register --username saywankarpranay --password Lkjhgfdsa@1234 --auto-attach

5  yum upgrade

6  subscription-manager repos --enable=rhel-7-server-extras-rpms

7  yum update

8  swapoff -a

9  nano /etc/fstab

10  hostnamectl

11  nano /etc/hosts

12  exec bash

13  nano /etc/network/interfaces

14  ls /etc/networks

15  ls /etc/networks /

16  ls /etc/networks/

17  cat /etc/networks

18  setenforce 0

19  sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux

20  sysctl -w net.ipv4.ip_forward=1

21  sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/g' /etc/sysctl.conf

22  sudo sysctl -p /etc/sysctl.conf

23  systemctl status firewalld

24  systemctl stop firewalld

25  systemctl status firewalld

26  systemctl status iptables

27  systemctl status iptablesd

28  nano /etc/sysctl.conf

29  sestatus

30  sysctl -p

31  cat > /etc/modules-load.d/containerd.conf <<EOF
overlay
br_netfilter
EOF


32  modprobe overlay

33  modprobe br_netfilter

34  cat > /etc/sysctl.d/99-kubernetes-cri.conf <<EOF
net.bridge.bridge-nf-call-iptables  = 1
net.ipv4.ip_forward                 = 1
net.bridge.bridge-nf-call-ip6tables = 1
EOF



35  sysctl --system

36  yum install yum-utils device-mapper-persistent-data lvm2

37  yum-config-manager     --add-repo     https://download.docker.com/linux/centos/docker-ce.repo

38  yum update && yum install containerd.io

39  mkdir -p /etc/containerd

40  containerd config default > /etc/containerd/config.toml

41  systemctl restart containerd

42  nano /etc/containerd/config.toml

43  cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF



44  setenforce 0

45  sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

46  yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes

47  systemctl enable --now kubelet

48  cat <<EOF >  /etc/sysctl.d/k8s.conf

net.bridge.bridge-nf-call-ip6tables = 1

net.bridge.bridge-nf-call-iptables = 1

EOF



49  sysctl --system

50  lsmod | grep br_netfilter

51  modprobe br_netfilter

52  cat <<EOF >  /etc/sysctl.d/k8s.conf

net.bridge.bridge-nf-call-ip6tables = 1

net.bridge.bridge-nf-call-iptables = 1

EOF



53  sysctl --system

54  kubeadm init --pod-network-cidr=192.168.0.0/16

55  mkdir -p $HOME/.kube

56  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

57  sudo chown $(id -u):$(id -g) $HOME/.kube/config

58  kubectl get pods -o wide --all-namespaces

59  kubectl apply -f https://docs.projectcalico.org/v3.8/manifests/calico.yaml

60  kubectl get pods -o wide --all-namespaces

61  kubectl get pods -o wide --all-namespaces

62  kubectl get pods -o wide --all-namespaces

63  kubectl get pods -o wide --all-namespaces

64  kubectl get pods -o wide --all-namespaces

65  kubectl taint nodes --all node-role.kubernetes.io/master-

______________________________________________________________

66  kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml

67  kubectl get pods -o wide --all-namespaces

68  kubectl get pods -o wide --all-namespaces

69  kubectl create serviceaccount dashboard -n default

70  kubectl create clusterrolebinding dashboard-admin -n default --clusterrole=cluster-admin --serviceaccount=default:dashboard

71  kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --
decode

72  kubectl get nodes
73  kubectl get deploment
74  kubectl get deploments
75  kubectl get deployments
76  kubectl get deployment
77  kubectl version
78  kubectl run kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1 --port=8080
79  kubectl get deployments
80  echo -e "\n\n\n\e[92mStarting Proxy. After starting it will not output a response. Please click the first Terminal Tab\n";
81  kubectl proxy
82  curl http://localhost:8001/version
83  kubectl get deployments
84   cd /var/log/
85  ls
86  cat vmware-vmsvc.log
87  vi yum.log
88  kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
89  history
