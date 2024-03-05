In mysql
    We want master to come first then worker1, worker2

For such deployment: we need statefulSet
* pods are created in sequencial order
* assign unique index to each pod (maintain sticky identity)


initial 3
1
2
3

scale to 5
1 2 3 4 5

scale to 2
1 2

you can avoid ordered creation to setting podManagementPolicy: Parallel
