# Pod-with-Secret-K8
Kubernetes Secrets let you store and manage sensitive information, such as passwords, OAuth tokens, and ssh keys.

Simple example to demonstrate use of Secret in a Pod-

Steps followed:

*As Root*
```
1. Create the secret with some key and values and checkout the secret created.
$ kubectl create secret generic --from-literal ROOT_PASSWORD=rootpassword --from-literal DATABASE=db --from-literal USER=user --from-literal PASSWORD=password mysecret
$ kubectl get secret mysecret 

2. Create a Pod which uses the secret.
$ vi pod_with_secret.yaml
$ kubectl apply -f pod_with_secret.yaml

3. Checkout the secret being used by the Pod.
kubectl exec mysql-pod-with-secret -- printenv

Quick tip-
Once you have created secret you can decode it in the below manner-

1. Output the encoded value
$ kubectl get secret mysecret -o yaml

2. Decode the encoded value
$ echo "<encoded value>" | base64 --decode

```
*As Root*
