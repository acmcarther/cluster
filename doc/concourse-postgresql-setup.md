# Concourse Postgresql Setup

Forward connection to postgres
```
$ export POD_NAME=$(kubectl get pods --namespace default -l "app=postgres" -o jsonpath="{.items[0].metadata.name}")
$ kubectl port-forward $POD_NAME 5432:5432
```

Connect to postgres
```
psql -h localhost -U postgres
```

Set up databases and account
```
postgres=# create database atc;
CREATE DATABASE
postgres=# create database concourse;
CREATE DATABASE
postgres=# create user concourse password 'put-a-password-here'
```
