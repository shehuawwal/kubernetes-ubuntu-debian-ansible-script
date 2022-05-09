# Setup Kubernetes Cluster On Ubuntu/Debian

Clone The Repo

1 - Edit edit the hosts file with your server IP
2 - Edit The 0_host_config.sh file with your server IP and Hostname
3 - Then execute: ansible-playbook one_hostname-playbook.yaml
4 - Then execute: ansible-playbook two_disable-playbook.yaml
    Note: This Will Reboot The Server
5 - Then execute: ansible-playbook three_kubernetes-playbook.yaml

On The Master Node:
Login As Root

kubeadm init

Exit Root Account And Run
1 - mkdir -p $HOME/.kube
2 - sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
3 - sudo chown $(id -u):$(id -g) $HOME/.kube/config
4 - kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
5 - sudo kubeadm token create --print-join-command
6 - Copy The Token And Apply It On All The Worker Node Using

References
[+] https://shehuawwal.com/building-a-kubernetes-cluster-from-scratch-with-kubeadm/