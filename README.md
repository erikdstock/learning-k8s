# K8S Cluster Playground

Reference links (as of kubernetes 1.16):
- [Kubernetes object management concepts](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/)
- [kubectl book](https://kubectl.docs.kubernetes.io/)
- [API Conventions](https://github.com/kubernetes/community/blob/e24c344aa32cdf87b4703c52e9af799795a54b37/contributors/devel/sig-architecture/api-conventions.md#spec-and-status)
- [Generated docs](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/#pod-v1-core)
Tutorials:
- [kubernetes.io tutorials](https://kubernetes.io/docs/tutorials/)
- [getting started with kubernetes (digital ocean)](https://www.digitalocean.com/community/meetup_kits/getting-started-with-containers-and-kubernetes-a-digitalocean-workshop-kit)

## Setup:

- Download kubectl version matching your cluster
- Put cluster config in `kubeconfig.yaml` (gitignored)
- `export KUBECONFIG='./kubeconfig.yaml'`

## Experiments

### Deploy an image

Using [n8n](https://github.com/n8n-io/n8n/blob/e0752b861de8f21795dd2494ca0167b3091e2483/docker/images/n8n/README.md) as a guinea pig

```sh
# Deploy the n8n image
kubectl create deployment n8n-web --image=n8nio/n8n
# Access it locally at localhost:8000 (n8n runs on 5678)
kubectl port-forward deployment/n8n-web 8000:5678
# - Change and save data in the interface (eg edit and save workflow and create another)
# Get pods
kubectl get pods
# delete pod from the output
kubectl delete pod n8n-web-<blah-blah-blah>
# -> After a moment the pod will be back (due to deployment configuration) but you will have lost your stored workflows
```
