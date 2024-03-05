AdmissionControl is plugin based
===============================================================
enable-admission-plugins
disable-admission-plugins

===============================================================

kubectl describe pod kube-apiserver-controlplane -n kube-system | then grep for kube-apiserver
kube-apiserver -h | grep enable-admission-plugins

kubectl exec kube-apiserver-controlplane -n kube-system -- kube-apiserver -h | grep enable-admission-plugins

--enable-admission-plugins=NodeRestriction,NamespaceAutoProvision (NameSpaceLifecycle - new )

it can change the request itself. 
for looking you can also use

ps -ef | grep kube-apiserver | grep admission-plugins

======================================================================
updating admission control

Add NamespaceAutoProvision admission controller to --enable-admission-plugins list to /etc/kubernetes/manifests/kube-apiserver.yaml
It should look like below

    - --enable-admission-plugins=NodeRestriction,NamespaceAutoProvision
API server will automatically restart and pickup this configuration.

======================================================================
Mutating admission control -that check the request (this runs first then comes the validating)
Validating admission control -that validate the request

======================================================================
Mutating Admission webhook
Validating Admission webhook

webhook:
* Deploy webhook (can be deloyed in k8s itself)
