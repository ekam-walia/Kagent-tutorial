Let's create a Deployment with 3 Pods

```bash
kubectl create deployment nginx \
  --image=nginx \
  --replicas=3
```

```bash
kubectl get pods
```

Now Intentionally break the deployment 

```bash
kubectl set image deployment/nginx nginx=nginx:does-not-exist
```

```bash
kubectl get pods
```

Now ask Kagent on the localhost instance that why is not my Pod working

```text
Why is the nginx pod stuck in ImagePullBackOff? Investigate the Deployment, Pods, ReplicaSets and events. Identify the root cause. Do not modify anything yet.
```