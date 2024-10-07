# Istio_ServiceMesh

Istio is service mesh.
Service Mesh manages communication between microservices.

Challenges of Microservice Architecture
1. There are multiple microservice application like for eg in Ecommerce site we have - Online Website, Cart, Payment, etc. This all are dependent and there must be some communication between them that is where service mesh helps you need to add endpoint so that it knows which application/pod can talk to newly added Pod. we have comm.config (communication configuration).
2. Security prespective, even if cluster is secured using proxy, firewalls, etc - Once your request enters the cluster, it can do lot of illegal things bcoz communication inside cluster is not secure, every service inside the cluster can talk to any other service.
   
These non business logic must be added to each application -
comm.config  ( Communication Configuration )
security logic ( security inside cluster )
retry logic ( after failing connection it need retry logic by developers )
metrics ( Metrics for each service )
tracing ( Tracing means how many http requests are coming to each service )

Solution - Service Mesh with Sidecar pattern

SideCar proxy
- Handles these networking logic
- Acts as a proxy
- Its Third-Party Application
- Cluster operators can configure it easily
- Control Plane has ability to inject the Sidecar proxy on each Microservice Pod
  
Traffic Splitting
- Suppose we have new version of payment application, we did testing and all necessary things needed still you can't be sure that there is NO Bug.
- Instead you can send 1,5, 10% of traffic to new version and gradually increase it ( Canary deployment ).
  
<img width="1023" alt="image" src="https://github.com/user-attachments/assets/0996f88b-3167-4bb6-922e-41d65bd15ea1">


