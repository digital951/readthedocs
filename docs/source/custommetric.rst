Horizontal auto scaling based on a custom metric
=====

Setting up horizontal auto scaling based on a custom metric in Kubernetes requires several steps:

1. **Install Metrics Server**

   Kubernetes Metrics Server is a scalable, efficient source of container resource metrics. If you haven't installed the Metrics Server, you can do it by running the following command::

      .. code-block:: bash

         kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

   Verify the Metrics Server installation::

      .. code-block:: bash

         kubectl get deployment metrics-server -n kube-system

2. **Install and Configure Custom Metrics API**

   The Custom Metrics API is often provided by "adapter" applications, which translate the results from monitoring systems into the format expected by the Custom Metrics API. One of these is the Prometheus adapter.

   You can install the Prometheus adapter via Helm::

      .. code-block:: bash

         helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
         helm install [RELEASE_NAME] prometheus-community/prometheus-adapter

   Replace ``[RELEASE_NAME]`` with the name you want to give your Prometheus Adapter release.

3. **Set up Custom Metrics**

   With the adapter installed, you can set up your custom metrics. The Prometheus adapter can be configured to present the custom metrics you need. These are defined in a ConfigMap.

4. **Define Horizontal Pod Autoscaler**

   Once you have your custom metric set up and exposed via the adapter, you can create an HPA resource to use it. Below is an example of how you might set up an HPA resource using a custom metric::

      .. code-block:: yaml

         apiVersion: autoscaling/v2beta2
         kind: HorizontalPodAutoscaler
         metadata:
           name: my-app-hpa
         spec:
           scaleTargetRef:
             apiVersion: apps/v1
             kind: Deployment
             name: my-app
           minReplicas: 1
           maxReplicas: 10
           metrics:
           - type: Pods
             pods:
               metric:
                 name: my_custom_metric
               target:
                 type: AverageValue
                 averageValue: 50

   Replace "my_custom_metric" with the name of your custom metric. This HPA will maintain an average value of the custom metric of 50 per pod.

Please note that the setup process can be complex, and these are high-level steps. The specifics can vary depending on the infrastructure and the exact metric you're scaling on. Make sure to refer to the specific documentation for each tool you are using.
