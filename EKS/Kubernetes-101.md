Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.

- Cloud-agnostic. Can be used on-premises and within many public cloud platforms.

## Cluster Structure & Detail

Cluster: Highly available cluster of compute resources which are organized to work as one unit.

Control Plane: Manages the cluster, scheduling, applications, scaling, and deploying.

Cluster Nodes: A VM or physical server which functions as a worker in the cluster.
  - Each node runs `containerd` (or another container runtime) for handling container operations.
  - `kubelet` runs as an agent to interact with the cluster control plane.
  - Kubernetes API is used for communication between the control plane and a kubelet agent.

Pods: Smallest units of computing in Kubernetes Shared storage and networking. "one-container one-pod" is very common (although you can have more than one container per pod).
  - Pods are not permanent.
  - Generally you'd only run multiple containers in one pod if the containers are tightly coupled and require close proximity.

`kube-apiserver`: The frontend for the kubernetes control plane. It's what nodes and other cluster elements interact with. Can be horizontally scaled for HA and performance.

`etcd` provides a highly-available key value store used within the cluster. It's used as the main backing store for the cluster.

`kube-scheduler`: Identifiers any pods within the cluster with no assigned node and assigns a node based on resource requirements, deadlines, affinity/anti-affinity, data locality, and any other constraints.

`cloud-controller-manager`: Provides cloud-specific control logic. It allows you to link kubernetes with a cloud providers APIs.

`kube-controller-manager`: Cluster controller processes Node controller for monitoring and responding to node outages, Job controller for one off tasks (jobs => PODS), Endpoint controller for populating endpoints (services <=> PODS), and service account & token controllers for accounts/API tokens.

`kube-proxy` is a network proxy. Running on each node. It coordinates networking with the control plane. It helps implement "services" and configures rules allowing communications with pods from inside or outside of the cluster.

## Summary

Cluster: A deployment of Kubernetes, management, orchestration, ...

Node: Resources; pods are placed on nodes to run.

Pod: 1+ containers; Smallest unit in kubernetes; Often 1 container 1 pod.

Service: Abstraction, service running on 1 or more pods.

Job: Ad-hoc, creates one or more pods until completion.

Ingress: Exposes a way into a service (Ingress => Routing => Service => 1+ Pods).

Ingress Controller: Used to provide ingress (e.g. AWS Load Balancer Controller uses ALB/NLB)

Generally best to architect things in kubernetes to be stateless (pods are temporary). Any storage in kubernetes by default is ephemeral. If a pod moves between nodes, that storage is lost.

Persistent storage (PV): Volume whose lifecycle lives beyond any 1 pod using it.
