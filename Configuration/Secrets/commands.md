# General commands

`kubectl get secrets`

`kubectl get secrets -n safe recipe5 -o json`

echo "ZmxvdXIsIHN1Z2FyIGFuZCA1IGFwcGxlcw==" | base64 --decode

kubectl create secret generic my-secret --from-file=path/to/bar
kubectl create secret generic devops-secret --from-literal=username=azbykovskyi --from-literal=password=azbykovskyi_password --from-literal=email=azbykovskyi@lab.playpit.net

$ echo -n 'username' | base64 -w0
dXNlcm5hbWU=

$ echo 'dXNlcm5hbWU=' | base64 -d
username

$ echo -n 'admin' > username
$ echo -n '1f2d1e2e67df' > password

$ kubectl create secret \
  generic db-user-pass \
  --from-file=username \
  --from-file=password
