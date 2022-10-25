# k8sinit Workshop

## Log into k8s
First step, go to:
https://cloud.amoyel.fr/s/pJ7i2xTsCtHyb6e

When you have your credentials, go to:
https://gcm.init.amoyel.fr

Input your username and password

## Deploy webapp-color app
Custom manifests in ./manifests

Docker image sources on:
https://git.amoyel.fr/opsfinity/webapp-color

Apply manifests with:
```
cd manifests
kubectl apply -f ./
```

See results:
```
kubectl get all,ing
```

## Autoscaling
Apply hpa manifest:
```
kubectl apply -f ./hpa
```

Prepare visualization :
```
tmux
```
Do ```Ctrl + b + "```

Do ```Ctrl + b + UpArrow```

Do ```Ctrl + b + SHIFT + %```

In the first terminal:
```
watch 'kubectl top pods'
```
In the second:
```
watch 'kubectl get po'
```

And in the last:
```
ab -n 15000 -c 15 https://COLOR.init.amoyel.fr/
```

Now, you can see autoscaling in action ;)

# Cleanup
Simply delete resources:
```
kubectl delete -f ./
kubectl delete -f ./hpa
```