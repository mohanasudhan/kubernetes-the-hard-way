Package of custom resource defintion and custom controller is called operators
kubectl create -f flight-operator.yaml

Operator framework
etcd Operator
    - CRD
        - EtcdCluster
        - EtcdBackup
        - EtcdRestore
    - custom controller
        - etcd controller
        - backup operator
        - restore operator

All operator are available at OperatorHub.io
