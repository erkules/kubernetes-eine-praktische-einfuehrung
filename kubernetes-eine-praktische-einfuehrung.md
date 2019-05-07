# Kubernetes

Eine praktische Einführung

# Ich

erkan@linsenraum.de
twitter: @erkuleswastaken
xing/linkedin auch
https://devops-training.de/
https://devops-kubernetes-camp.de/
...
# Wieso Weshalb Warum?

* Orchestrierung?
* Orchestrierung++
* Kubernetes ist das neue RZ

# K8s Aufbau

Architekturbild

Was bekommen Container

* Flaches nodeüberspannendes internes Netzwerk
* DNS
* ...

# Art of Deployment

* Deklarativ (CI/CD)
* Lifecycle
* Anzahl der Rechner?

# Namespaces

* Logische Partitionierung
* Ermöglicht
* Netzerksegmentierung
* Multitenantsupport
* mit Ressourcenlimitierung
* ...

~~~
kubectl create ns jax
kubens jax <-- Ersetzt -n jax bei den folgenden Aufrufen
~~~

# Pods

* Kleinste Einheit
* VMs für Container

~~~
kubectl apply -f obj/pod.yml
kubectl exec -ti www sh 
~~~

Problem:

* Keine Replicas
* Kein HA
* Kein Skalieren



# Deployments

* HA
* Updatestrategien (heute abend)

~~~
kubectl apply -f obj/deployment.yml
~~~

* Skalieren

# Services

* Service Discovery
* Labels
* Interne VIP
* DNS

~~~
kubectl apply -f obj/deployment-svc.yml
~~~

# Ingress 

Große weite Welt:

~~~
obj/deployment-ing.yml
~~~

* Ein Rolling Update zeigen
* Deklarativ

# HA + Storage

Kleine Spielerei mit Storage

~~~
kubectl apply -f obj/mysql-pvc.yml           <-- pvc
kubectl apply -f obj/mysql-deploy.yml        <-- Datbenbank
kubectl apply -f obj/mysql-svc.yaml          <-- Service
kubectl exec ..
kubectl apply -f obj/mysql-client-deploy.yml  <-- Client
kubectl apply -f obj/mysql-client-svc.yml     <-- Service
kubectl apply -f obj/mysql-client-ing.yml     <-- Weite Welt
~~~

Failovern

~~~
 kubectl taint node <node>  sched=nono:NoSchedule
 kubectl taint node <node>  sched:NoSchedule-
~~~



# Kubernetes++

* Logs  (Loki)
* Metriken  (Prometheus)

Eigene Metriken?

~~~
kubectl apply -f obj/busybox-exporter.yml
~~~

# Noch so viel:

* Autoscaling
* Security
* Placements
* Netzwerkregeln
* Priorities
* StatefulSets/DaemonSets
* Configs/Secrets
* (Cron)Jobs
* ....

# SERVICE-MESH

https://landscape.cncf.io/category=service-proxy,api-gateway,service-mesh&format=card-mode&grouping=category


und ja Serverless/Faas


