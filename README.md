# Command to Run

```
ytt -f . 
```

# Output

```
apiVersion: carto.run/v1alpha1
kind: Workload
metadata:
  labels:
    app.kubernetes.io/part-of: sample-app
    apps.tanzu.vmware.com/workload-type: web
  name: sample-app
  namespace: jeremy
spec:
  params:
  - name: maven
    value:
      artifactId: demo
      groupId: com.example
      version: 0.0.2-SNAPSHOT
  resources:
    limits:
      cpu: 2000m
      memory: 4Gi
    requests:
      cpu: 2000m
      memory: 4Gi
  env:
  - name: mae-env
    valueFrom:
      configMapKeyRef:
        name: myconfigmap
        key: myconfigmapkey-1
  - name: jeremy-env
    valueFrom:
      secretKeyRef:
        name: mysecret
        key: mysecretkey-1
  - name: jeremy-env
    valueFrom:
      secretKeyRef:
        name: mysecret
        key: mysecretkey-2
```
