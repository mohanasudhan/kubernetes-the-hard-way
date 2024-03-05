CRD - It is an extension of the Kubernetes API that is not necessarily available in a default Kubernetes installation.
Then we want to create flightticket_controller.go

Above is customController

1. First define the resource (CRD - custom resource defintion)
2. create a custom controller (monitor, does some work and update)
e.g. kubernetes/sample-controller