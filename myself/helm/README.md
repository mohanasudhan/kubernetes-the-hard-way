Wordpress
* Deployment
* persistent volume
* persistent volume claim
* service
* secrets

General comment like
helm install wordpress  ...

It has values.yaml for all customization of the application

It also supports upgrade, rollback, uninstall

Since helm doesn't come with you cluster. use snap command to install helm

sudo snap install helm --classic ( install in the dev setup and also have kubectl ) --- for linux

for ubuntu:
curl https://baltocdn.com/helm/signing.asc | apt-key add -
apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | tee /etc/apt/sources.list.d/helm-stable-debian.list
apt-get update
apt-get install helm


# repo
default - artifacthub.io

helm search hub wordpress -> does search in default

But there are other repos as well

helm repo add bitnami https://charts.bitnami.com/bitnami
helm search repo joomla 
helm repo list

# installation
helm install [release-name] [chart-name]

release-name - name

# only download don't install

helm pull --untar bitnami/wordpress