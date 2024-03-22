1. Kubernates is open source container orchestration tool. Developed by google
2. It will help you manage containerized applications in different deployment environment like
    a. Physical
    b. Virtual
    c. Cloud
    d. Hybrid

## What features do orchestration tools offer?
1. High availability or no downtime
2. Scalability or high performance.
3. Disaster recovery backup and restore.

Kubernates Components
1. Node
2. Pod
    Smallest unit of k8's
    Abstraction over container
    usually 1 application per pod
    Each pod gets its own IP address
    New IP address on re-creation

3. Service
    Permanent IP address
    Each pod will have their own service.
    lifecycle of pod and service NOT connected
    Types of services
        External Service (https://my-app.com)
        Internal Service (http://db-service-ip:port)
4. Ingress : Domain forwarding to external service
5. ConfigMap : store external configuration of your application.
6. Secret : just like config map
    used to store secret data
    base64 encoded
7. Volums : Attach a physical storage to your pod.
    It can be either storage on local machine.
