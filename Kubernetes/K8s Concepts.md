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

