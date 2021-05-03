

# Helloworld service (istio retries example)

We will distribute load with retries within the scope of istio-example

Along with the timeout, there can be retry as well.
Because when the service dropped after the timeout is should retry sending the request so it won’t be dropped permanently.

This sample includes three versions(v1,v3) of a simple helloworld service that returns its project version when called. It can be used as a test service when experimenting with version routing.

This service is also used to demonstrate  retries deployments working in conjunction. See retries deployments using Istio. Code repo for image [github\dotnet-example](https://github.com/OktaySavdi/dotnet-example)

## Start the helloworld service

The following commands assume you have [automatic sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#automatic-sidecar-injection) enabled in your cluster. If not, you'll need to modify them to include [manual sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#manual-sidecar-injection).

Deploying version v1, v3 or both:
```ruby
oc create -f Retries_Example/
```
![https://github.com/OktaySavdi/istio-examples/tree/master/Retries_Example](https://user-images.githubusercontent.com/3519706/76602764-b053e800-651c-11ea-95e1-543b5141a7c2.png)


## Generate load
```ruby
while true; do curl -s "http://[URL]/istio"; sleep 0.5; echo -e '\n'; done
    
while true; do curl -s "http://myapps.mycluster.com/istio"; sleep 0.5; echo -e '\n'; done 
```
## Monitoring and Control

Control istio Config

![image](https://user-images.githubusercontent.com/3519706/116877626-dcea2800-ac26-11eb-8e6a-53aeb8aad995.png)

**Control Graph**

![https://github.com/OktaySavdi/istio-examples/tree/master/Retries_Example](https://user-images.githubusercontent.com/3519706/76602846-d37e9780-651c-11ea-983f-40ee92eff74b.png)

**Overview Console**

![https://github.com/OktaySavdi/istio-examples/tree/master/Retries_Example](https://user-images.githubusercontent.com/3519706/73649574-1f722d00-4691-11ea-8f8f-f9ce8f21b4fa.png)

**Inbound Metrics**

![https://github.com/OktaySavdi/istio-examples/tree/master/Retries_Example](https://user-images.githubusercontent.com/3519706/73649621-3d3f9200-4691-11ea-9a4f-d12737d9c59a.png)

**CLI on Server**

![https://github.com/OktaySavdi/istio-examples/tree/master/Retries_Example](https://user-images.githubusercontent.com/3519706/76602971-1b052380-651d-11ea-997a-2118cd9704a3.png)
