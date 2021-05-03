# What is Istio Service Mesh?

We will distribute load with loadbalancing within the scope of istio-example

Istio service mesh provides several capabilities for traffic monitoring, access control, discovery, security, resiliency, and other useful things to a bundle of services. It delivers all that and strikingly does not require any changes to the code of any of those services.

# The Istio Service Mesh Architecture

-   Istio service mesh is an intentionally designed abstraction that has both a control plane and a data plane.
-   Istio is a service mesh created by the combined efforts of IBM, Google, and Lyft. The sidecar patterns are enabled by the Envoy proxy and are based on containers.

![image](https://user-images.githubusercontent.com/3519706/116872101-fe92e180-ac1d-11eb-80fc-305583cf7a01.png)

**Envoy**

-   Envoy is an open-source extension and service proxy provider, built for cloud-extensive meshes. The Istio mesh creates an extendible proxy system through Envoy.

**Mixer**

-   The mixer is a part of the service mesh that helps in enforcing safety protocols, allowing access controls and implementing usage policies and works independently from the mesh.

**Pilot**

-   Pilot provides all services for the Istio Envoy sidecars and allows for a more coherent traffic management system with high level routing.

**Citadel**

-  Performs TLS certificate management

**Galley**

-  It offers configuration management services for Istio.

**Telemetry**

-  Collects statistics on machines
