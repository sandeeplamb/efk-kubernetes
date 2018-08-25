# EFK-Kubernetes

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