Kernel
it is the main part of operating system.
manages resources, facilitating communication between hardware and software components.

WSL2
it is a software feature or component. it's integrated with windows.
it allows users to run any linux distribution alongside windows installation.

docker kubernetes: https://www.youtube.com/watch?v=kTp5xUtcalw
cloud native: https://aws.amazon.com/what-is/cloud-native/#:~:text=The%20term%20cloud%20native%20refers,container%20orchestrators%2C%20and%20auto%20scaling.
WSL https://www.youtube.com/watch?v=av0UQy6g2FA
linux packages https://www.youtube.com/watch?v=yxc2ntmH9xY

project idea :- plugin to take snapshot of all tabs open at a point of time with url and save


x86 ARM - type of architecture of computer processor

Minikube
minikube provisions and manages local Kubernetes clusters optimized for development workflows.

the above line literally comes up when you prompt minikube in terminal.

minikube - creates a cluster from scratch
kubectl - manage your cluster.

So while using any cloud provider, aws, gcp, azure, their command to create a minikube has to be used and kubectl for all other things.

Gitops -
IaC - Infrastructure as Code

Kubernets namespaces let you isolate and organize your workloads.

> Deployments

The goal of kubernetes is to make our application highly available.
there are multiple replicas of the application running at the same time, if one instance goes 
down so we have others to fallback on.
our application runs on something called as a kubernetes pod.
a pod can contain one or more containers.
so we can organize pods using kubernetes deployment. 
Taking an example of deployment.yaml file, 3 pods are deployed containing the same container.
So, if one of the pod is shut down, another one is spun-off immediately.

> View logs
Using describe command.

> How to verify that the pod is up and running.
    using busybox. busybox has utilities like wget, whoami etc.


### Service

How can we access kubernetes cluster from the internet ? 
-> Kubernetes service.

3 types of service.
1. Cluster ip 
2. Node port 
3. Load balancer 

So the command minikube tunnel creates a network route between the minikube virtual machine and the host machine. So it allows external traffic to reach services within the minikube cluster.

Adding resource requests and limits to the pod.

So a pod acquires memory and cpu resources and overtime it can cause an outage if it exceeds the capacity of the pod. so we set a minimum and maximum limit

resources:
    requests: #minimum - do not schedule a pod unless acquired this
        memory: "64Mi"
        cpu: "250m"
    limits: # stop if consumes more than this.
        memory: "128Mi"
        cpu: "500m"

### Theory

instance of kubernetes is called a cluster.
-> each cluster has control plane and atleast one worker node.

kubernetes & control plane is like airport and air traffic control.

control plane takes care that the pods are created modified and deleted without any issue.

Control Plane contents
    - kube api server
      - entrypoint for all requests.
      - pods deployments all have api endpoints.
      - this has a rest interface.
      - kubectl and kubeadm are CLI tools to communicate with Kubernetes API via HTTP requests.
    - etcd:
      - etcd is a distributed key-value stor
      - also can run as a pod
    - sched 
      - assigns a worker node to the cluster
    - controller manager
      - if some node gets down - replacing such nodes.
      - clean up and all.
    - cloud controller manager
      - to interact with cloud service providers.
Worker nodes
    - pods are scheduled and run. 
    - Components
      - kubelet - agent
      - makes sure container in a pod are running and healthy.


Stateful storage - kubernetes persistent storage.
