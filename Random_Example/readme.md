
# Helloworld service (istio random example)

We will distribute load with random within the scope of istio-example

This sample includes two versions(v1,v2,v3) of a simple helloworld service that returns its project version when called. It can be used as a test service when experimenting with version routing.

This service is also used to demonstrate random deployments working in conjunction. See random deployments using Istio. Code repo for image [github\dotnet-example](https://github.com/OktaySavdi/dotnet-example)

## Start the helloworld service

The following commands assume you have [automatic sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#automatic-sidecar-injection) enabled in your cluster. If not, you'll need to modify them to include [manual sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#manual-sidecar-injection).

Deploying version v1, v2, v3 or both:

    oc create -f Random_Example/
![https://github.com/OktaySavdi/istio-examples/tree/master/Random_Example](https://user-images.githubusercontent.com/3519706/74038548-78afc880-49d1-11ea-93df-bd08300e1009.png)


## Generate load
```bash
istio_ingress="$(kubectl get svc istio-ingressgateway --namespace istio-system --output 'jsonpath={.spec.ports[?(@.port==80)].nodePort}')"
    
while true; do curl -s "http://[URL]/istio"; sleep 0.5; echo -e '\n'; done
    
while true; do curl -s "http://myapps.mycluster.com/istio"; sleep 0.5; echo -e '\n'; done 
```
## Monitoring and Control

Control istio Config

![image](https://user-images.githubusercontent.com/3519706/116877626-dcea2800-ac26-11eb-8e6a-53aeb8aad995.png)

**Control Graph**

![https://github.com/OktaySavdi/istio-examples/tree/master/Random_Example](https://user-images.githubusercontent.com/3519706/74130884-2f8b8e80-4bf4-11ea-8abc-3b808256dd59.png)

**Overview Console**

![https://github.com/OktaySavdi/istio-examples/tree/master/Random_Example](https://user-images.githubusercontent.com/3519706/73649574-1f722d00-4691-11ea-8f8f-f9ce8f21b4fa.png)

**Inbound Metrics**

![https://github.com/OktaySavdi/istio-examples/tree/master/Random_Example](https://user-images.githubusercontent.com/3519706/73649621-3d3f9200-4691-11ea-9a4f-d12737d9c59a.png)

**CLI on Server**

![https://github.com/OktaySavdi/istio-examples/tree/master/Random_Example](https://user-images.githubusercontent.com/3519706/74039639-3f785800-49d3-11ea-8698-119d265a704c.png)

