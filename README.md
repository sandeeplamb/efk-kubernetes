# EFK-Kubernetes

The current kubernetes EFK stack needs to be modified in order to deploy out-of-the-box.

I have ameneded the below files in order to work EFK stack OOB.

1. Updated file `es-statefulset.yaml` to add volumeClaimTemplate and Storage-Class.
2. Updated file `fluentd-es-ds.yaml` to remove Node-Selector.
3. Updated file `kibana-deployment.yaml` to remove env variable.

You might need to add the Storage-Class and change the name of `storageClassName` in `volumeClaimTemplates` in file `es-statefulset.yaml`

```
volumeClaimTemplates:
  - metadata:
      name: elasticsearch-logging
    spec:
      accessModes: ["ReadWriteOnce"]
      storageClassName: gp2
      resources:
        requests:
          storage: 1Gi
```

## Install EFK Stack

`kubectl apply -f .`

## Find Kibana EndPoint

`kubectl cluster-info`