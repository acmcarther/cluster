# setup-nodes

Initialize master
```
$ kubeadm init
```

Override default kube-proxy image
```
# TODO
```

Copy ./kube/config to local machine
```
# TODO
```

Initialize Workers
```
$ kubeadm join --token xxxxx.xxxxxxxxxxxxxxx
```

Start Weave, Kubernetes console, and other kube-system level jobs
```
$ kubectl apply -R -f ./deploy/roles/kube-system.yaml
$ kubectl apply -R -f ./deploy/jobs/kube-system
```

Label storage nfs node
```
# TODO
```

Start storage
```
$ kubectl apply -f ./deploy/roles/storage.yaml
$ kubectl apply -R -f ./deploy/jobs/storage/
```

Make sure that provisioner job has started without incident
```
$ kubectl proxy
# Visit dashboard on localhost
```

Set up secrets
```
# In ./deploy/secrets, make production copies and edit secrets.
```

Start the rest of the jobs:
```
$ kubectl apply -R -f ./deploy/configs
$ kubectl apply -R -f ./deploy/secrets
$ kubectl apply -R -f ./deploy/roles
$ kubectl apply -R -f ./deploy/pvcs
$ kubectl apply -R -f ./deploy/jobs
```
