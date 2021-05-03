


# Helloworld service (istio delay example)

We will distribute load with delay within the scope of istio-example

This sample includes two versions(v1,v2,v3) of a simple helloworld service that returns its project version when called. It can be used as a test service when experimenting with version routing.

This service is also used to demonstrate  delay deployments working in conjunction. See delay deployments using Istio. Code repo for image [github\dotnet-example](https://github.com/OktaySavdi/dotnet-example)

## Start the helloworld service

The following commands assume you have [automatic sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#automatic-sidecar-injection) enabled in your cluster. If not, you'll need to modify them to include [manual sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#manual-sidecar-injection).

Deploying version v1, v2, v3 or both:

    oc create -f Delay_Example/
    
![https://github.com/OktaySavdi/istio-example/tree/master/Delay_Example](https://user-images.githubusercontent.com/3519706/74216116-6d4fec00-4cb4-11ea-9b9b-4c0882cc762f.png)

## Generate load

    while true; do curl -s "http://[URL]/istio"; sleep 0.5; echo -e '\n'; done
    
    while true; do curl -s "http://myapps.mycluster.com/istio"; sleep 0.5; echo -e '\n'; done 

## Monitoring and Control

Control istio Config

![image](https://user-images.githubusercontent.com/3519706/116877626-dcea2800-ac26-11eb-8e6a-53aeb8aad995.png)

**Control Graph**

![https://github.com/OktaySavdi/istio-example/tree/master/Delay_Example](https://user-images.githubusercontent.com/3519706/74215996-0e8a7280-4cb4-11ea-9465-eb700502acd3.png)

**Overview Console**

![https://github.com/OktaySavdi/istio-example/tree/master/Delay_Example](https://user-images.githubusercontent.com/3519706/73649574-1f722d00-4691-11ea-8f8f-f9ce8f21b4fa.png)

**Inbound Metrics**

![https://github.com/OktaySavdi/istio-example/tree/master/Delay_Example](https://user-images.githubusercontent.com/3519706/73649621-3d3f9200-4691-11ea-9a4f-d12737d9c59a.png)

**CLI on Server**

![https://github.com/OktaySavdi/istio-example/tree/master/Delay_Example](https://user-images.githubusercontent.com/3519706/74216221-bd2eb300-4cb4-11ea-88e7-4ad0337f4aea.png)

or try with siege

    wget -c https://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/s/siege-4.0.2-2.el7.x86_64.rpm https://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/l/libjoedog-0.1.2-1.el7.x86_64.rpm -P installation
    
    rpm -ivh installation/*.rpm

    siege --version

**Siege Load**
```json
siege -r 10 -c 4 -v http://deneme.10.10.10.10.nip.io:30889/
```

![https://github.com/OktaySavdi/istio-example/tree/master/Delay_Example](https://user-images.githubusercontent.com/3519706/74216052-3da0e400-4cb4-11ea-8af8-1e0e3943cdbf.png)

