## Docker and Kubernetes Course

https://codewithdan.com/products/docker-kubernetes

View the **Kubernetes for Developers: Core Concepts** video course on Pluralsight:

https://app.pluralsight.com/library/courses/kubernetes-developers-core-concepts/table-of-contents




kubectl -n kube-system create serviceaccount kubeconfig-sa
kubectl create clusterrolebinding add-on-cluster-admin --clusterrole=cluster-admin --serviceaccount=kube-system:kubeconfig-sa

apiVersion: v1
kind: Secret
metadata:
  name: oke-kubeconfig-sa-token
  namespace: kube-system
  annotations:
    kubernetes.io/service-account.name: kubeconfig-sa
type: kubernetes.io/service-account-token


kubectl apply -f oke-kubeconfig-sa-token.yaml


kubectl describe secrets oke-kubeconfig-sa-token -n kube-system


kubectl run my-nginx --image=nginx:alpine

kubectl port-forward my-nginx 8080:80

kubectl delete pod my-nginx