# Deploy

Contains kube configuration files. For now, they're raw yaml files.


## Organization

### Configs

Primarily configsets. Should ideally be pushed by a monitoring job as soon as committed, but currently human pushed.

### Jobs

Deployments, pods, services, service accounts. Should be pushed automatically on a release schedule configured somewhere else (something similar to google internal infrastructure).

### Pvcs

Storage for jobs. Ideally not human pushable at all, as I feel there is high risk in accidentally descheduling storage.

### Roles

All role declarations. Ought to not be human pushed at all.


## Push Practices

Typically `kubectl apply -R -f ./jobs` or variants is what is used. Take care using the `-R` recursive flag against the PVC directory.


## Alternatives Considered

### Templates

Deferred for now, as I don't expect to server multiple versions of the same services. If i start separating prod and sandbox work I'll re-evaluate.

### Ksonnet

Too much recent churn in github.com/ksonnet. As of time of writing, code just recently moved from /kubecfg into /ksonnet. Deduplication provided by ksonnet would be very helpful though.

### Helm

Too hands off for my tastes, and not sufficiently declarative. Basically "too much magic", and not enough gain for the magic. Dependent charts isn't an interesting feature for me, as I want to have full control over all runnning deployments, opting not to spin up MySql as soon as service X wants it, for example.
