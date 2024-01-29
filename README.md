# Kubernetes Cluster using Vagrant

## Hit the Star! ⭐
If you are planning to use this DevOps-Observability FOSS Stack repo for learning, please hit the star. Thanks!

## Setup

1. After cloning, as prerequisite install the vagrant & hypervisor on your local ubuntu machine

    ```bash
    $ sudo apt-get update
    $ sudo apt-get install vagrant
    $ sudo apt-get install virtualbox
    ```

2. Once you've installed both we can spinup the vm's using vagrant

    ```bash
    $ vagrant up
    ```
   This will take sometime, Since new vm's will be booted & bootstrapped using the script common.sh for installing crio, kubeadm, kubelet, kubectl with version of 1.28 k8's installed.

3. Once it's done. Let's initialize the masternode.

    ```bash
    $ vagrant ssh master-node
    $ kubeadm init --config=kubeadm-config.yaml
    ```
    This will take sometime, After getting a successfull initialization message

   To start using your cluster, you need to run the following as a regular user:
  ```bash
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
  ```
Alternatively, if you are the root user, you can run:
  ```bash
    export KUBECONFIG=/etc/kubernetes/admin.conf
  ```
Use the join command in the other 2 vm's
   
