# Helloworld service (istio canary example)

We will distribute load with canary within the scope of istio-example

This sample includes two versions(v1,v2) of a simple helloworld service that returns its project version when called. It can be used as a test service when experimenting with version routing.

This service is also used to demonstrate canary deployments working in conjunction. See canary deployments using Istio. Code repo for image [github\dotnet-example](https://github.com/OktaySavdi/dotnet-example)

## Start the helloworld service

The following commands assume you have [automatic sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#automatic-sidecar-injection) enabled in your cluster. If not, you'll need to modify them to include [manual sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#manual-sidecar-injection).

Deploying version blue, green or both:
```ruby
oc create -f Canary_Example/
```
![image](https://user-images.githubusercontent.com/3519706/116878485-1b341700-ac28-11eb-8ce2-a0359134c38a.png)

## Generate load
```ruby
while true; do curl -s "http://[URL]/istio"; sleep 0.5; echo -e '\n'; done
    
while true; do curl -s "http://myapps.mycluster.com/istio"; sleep 0.5; echo -e '\n'; done 
```
## Monitoring and Control

Control istio Config

![image](https://user-images.githubusercontent.com/3519706/116877626-dcea2800-ac26-11eb-8e6a-53aeb8aad995.png)

**Control Graph**

![https://github.com/OktaySavdi/istio-examples/tree/master/Canary_Example](https://user-images.githubusercontent.com/3519706/74132670-1a186380-4bf8-11ea-83d6-876c9fcb7960.png)

**Overview Console**

![https://github.com/OktaySavdi/istio-examples/tree/master/Canary_Example](https://user-images.githubusercontent.com/3519706/73649574-1f722d00-4691-11ea-8f8f-f9ce8f21b4fa.png)

**Inbound Metrics**

![https://github.com/OktaySavdi/istio-examples/tree/master/Canary_Example](https://user-images.githubusercontent.com/3519706/73649621-3d3f9200-4691-11ea-9a4f-d12737d9c59a.png)

**Weight**

![https://github.com/OktaySavdi/istio-examples/tree/master/Canary_Example](https://user-images.githubusercontent.com/3519706/74033776-f4a51300-49c7-11ea-9b86-48cdac52ab62.png)

**CLI on Server**

![https://github.com/OktaySavdi/istio-examples/tree/master/Canary_Example](https://user-images.githubusercontent.com/3519706/74032997-506e9c80-49c6-11ea-9784-6d03ad26fe9c.png)
