####  In this repo we will create the roboshop application using Helm packages


#### General Information

    we know that we add jenkins.repo and docker.repo to etc/yum.repo/jenkins.repo and then install the jekins directly by giving the command dnf install jenkins -y

    Similarly, if we want another opensource aplications to be deployed on k8s via heml, we place the helm.repo in the same etc/yum.repo location on a RHEL machine and directly execute the helm installation command

    Here, in our Roboshop project we are going to create the DBs using StatefulSets which require the csi drivers on the cluster.
    So, to install the drivers we can add th helm repo to etc/yum.repo and run helm installation command at the end.

    https://github.com/kubernetes-sigs/aws-ebs-csi-driver/blob/master/docs/install.md  >>> url where we will find the commands to add the helm rep to yum.repo

    Commands
    helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver

    helm repo update

    helm upgrade --install aws-ebs-csi-driver \
    --namespace kube-system \
    aws-ebs-csi-driver/aws-ebs-csi-driver

    Note:- Donot forget to add the EBS Policy at the SG of the nodes which we are using in our cluster as we are creating the EBS dynamically