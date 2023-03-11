Open-Source Container Orchestration


## Concepts

![[Kubernetes Architecture.png]]

The master (control plane) provides:
- Interaction with things outside the cluster (admin, e.g.) via REST API
- Communication with minions via REST API as well
- etcd service, a key-value store for shared state and configuration information
- Replication controller and scheduler
	- Maintains application's desired state
	- Scales application and rolls out updates
	- Schedules pods to run on nodes

The minion runs:
- kubelet, which communicates with the control plane and maintains pods
- kube-proxy, which funnels incoming connections to public services
- A container runtime (e.g. docker, podman)

Services are an abstraction and have a permanent IP address.
Pods are abstractions over one or more individual containers that run the app in question.
Each pod gets its own IP. When a pod dies, more are started with new IP addresses.

A minimum of 3 nodes is normally required for production. More control plane nodes are desirable to mitigate risk.

## Kubernetes Deployments
Instructs k8s how to create and update instances of an app
K8s control plan schedules application instances included in deployment to run on nodes.

Deployment controller monitors instances.
- If node goes down or is deleted, replaces instance with one on another node

Need:
	- container image
	- number of replicas

```R
bectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080

kubectl expose deployment hello-node --type=LoadBalancer --port=8080

kubectl delete service hello-node

kubectl delete deployment hello-node
```


## Pods
Group of one or more application containers and some shared resources:
- Shared storage - Volumes
- Networking - Unique cluster IP
- Information about how to run each container (image version, ports)

## Services
Exposes the application to the network outside the cluster
- labels and selectors - List the set of pods targeted by the service
	- labels are key/value pairs attached to objects
		- Designate objects for dev/test/prod
		- Embed version tags
		- Classify an object using tags
	- When not used, no endpoints object is created. Can manually map service to specific endpoints.
- Type
	- ClusterIP (default) - exposes on an internal IP in the cluster - only reachable from within cluster
	- NodePort - Exposes service on same port of each node using NAT. Accessible from outside using NodeIP:NodePort 
	- LoadBalancer: Creates external load balancer and assigns fixed, external IP
	- ExternalName: Maps service to contents of ExternalName field by returning a CNAME. No proxying of any kind is set up. Requires kube-dns v1.7 or CoreDNS 0.0.8+

---
# Source
[Learn Kubernetes Basics | Kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

# Left Off
[Viewing Pods and Nodes | Kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/)