# K8s commands examples

## Basic one

kubectl get configmap (cm)

kubectl describe configmap (cm)

kubectl create configmap my-config --from-file=path/to/bar

---
$ cat configmap/game.properties
enemies=aliens
enemies.cheat.level=noGoodRotten
lives=3

$ cat configmap/ui.properties
color.good=purple
color.bad=yellow
allow.textmode=true

kubectl create configmap game-config --from-file=configmap/

kubectl get cm game-config -o yaml
apiVersion: v1
data:
  game.properties: |
    enemies=aliens
    enemies.cheat.level=noGoodRotten
    lives=3
  ui.properties: |
    color.good=purple
    color.bad=yellow
    allow.textmode=true
kind: ConfigMap
metadata:
  ...

kubectl get cm game-config -o jsonpath='{.data.game\.properties}'
enemies=aliens
enemies.cheat.level=noGoodRotten
lives=3

---

$ kubectl create cm palitra --from-literal=RED="#FF0000" --from-literal=GREEN="#00FF00"
$ configmap/palitra created

$ kubectl get cm palitra -o yaml
apiVersion: v1
data:
  GREEN: '#00FF00'
  RED: '#FF0000'
kind: ConfigMap
metadata:
  ...

$ kubectl get cm palitra -o jsonpath='{.data.RED}'
'#FF0000'
