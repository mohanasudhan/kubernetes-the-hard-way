API groups
==============================================================================
alpha = very new like internal.apiserver.k8s.io/v1alpha1 

Alpha version is not enabled by default
It may lack end to end test
It may dropped after release
only available for expert who does alpha test

Beta
Enabled by default
no GA
few bugs

As of now FlowControlGroup is beta

GA
In this case it does not have alpha or beta in its version it is called v1
available to all users

apps, auth, are stable

==============================================================================
Even if the multiple versions are available for an API group only one will be preferred version

kubectl get deployment

In this case, it depend on the preferred version 

kubectl explain deployment (does provide preferred version)

Storage version is the version the object is stored in etcd - this requires to qurey etcd

To enable or disbale it is set it kube-apiserver parameter via --runtime-config=batch/v2alpha1

e.g, vi /etc/kubernetes/manifests/kube-apiserver.yaml
--runtime-config=rbac.authorization.k8s.io/v1alpha1

==============================================================================
DEPECRATION POLICY
==============================================================================
1. API elements may only be removed by incrementing the version of the API group

v1alpha1 -> course, webinar
v1alpha2 -> course

2. API objects must be able to round-trip between API version in a given release without information loss, with the exception of whole REST resources that do not exist in some versions (conversion from v2-> v1 should default values for new parameter)

deprecate older version

3. An API version in a given track may not be deprecated until a new API version at least as stable is released (example deprecration of v1 can be possible only when v2 is released, which should have gone to v2alpha1, v2alpha2, v2beta1, v2beta2)

4a. Other than the most recent API versions in each track, older API versions must be supported after their announced deprecation for a duration of no less than:

GA: 12 months or 3 releases (whichever is longer)
Beta: 9 months or 3 releases (whichever is longer)
Alpha: 0 releases


kubectl convert (its a plugin, you have to install 
e.g. curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl-convert
chmod +x kubectl-convert 
mv kubectl-convert /usr/local/bin/kubectl-convert
)

kubectl convert -f nginx.yaml --output-version apps/v1

kubectl explain job (to know more about an API)


What is the preferred version for authorization.k8s.io api group?
```
controlplane ~ ➜  kubectl proxy 8001&
[1] 8973

controlplane ~ ✦ ➜  Starting to serve on 127.0.0.1:8001
curl localhost:8001/curl localhost:8001/apis/authorization.k8s.io
{
  "kind": "APIGroup",
  "apiVersion": "v1",
  "name": "authorization.k8s.io",
  "versions": [
    {
      "groupVersion": "authorization.k8s.io/v1",
      "version": "v1"
    }
  ],
  "preferredVersion": {
    "groupVersion": "authorization.k8s.io/v1",
    "version": "v1"
  }
}
controlplane ~ ✦ 
```