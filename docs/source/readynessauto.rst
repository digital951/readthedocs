Autoscaling Based on Readyness
=====

Kubernetes uses several types of probes to determine the health and availability of pods, including readiness probes. Readiness probes tell Kubernetes when an application is ready to serve traffic. However, these probes themselves do not directly dictate autoscaling.

Autoscaling in Kubernetes typically relies on metrics like CPU usage or custom metrics provided by an application. It doesn't directly consider pod readiness states. The Horizontal Pod Autoscaler (HPA) in Kubernetes can scale the number of pods based on observed CPU utilization or on custom metrics.

However, if your application's readiness probe effectively represents its load or capacity to handle incoming requests, you could potentially use a custom metric for autoscaling.

Here is a basic example of how you might set up autoscaling based on CPU utilization:

1. Define the readiness probe in your pod specification::

   .. code-block:: yaml

      ...
      spec:
        containers:
          - name: my-container
            image: my-image
            readinessProbe:
              httpGet:
                path: /ready
                port: 8080
              initialDelaySeconds: 5
              periodSeconds: 5
      ...

2. Define an HPA for your deployment::

   .. code-block:: yaml

      apiVersion: autoscaling/v2beta2
      kind: HorizontalPodAutoscaler
      metadata:
        name: my-hpa
      spec:
        scaleTargetRef:
          apiVersion: apps/v1
          kind: Deployment
          name: my-deployment
        minReplicas: 1
        maxReplicas: 10
        metrics:
          - type: Resource
            resource:
              name: cpu
              target:
                type: Utilization
                averageUtilization: 50

In the HPA, ``my-deployment`` is the name of the deployment you want to autoscale. This HPA will maintain an average CPU utilization across all pods of 50%.

As previously mentioned, Kubernetes does not support autoscaling directly based on readiness probes. However, using custom metrics or by implementing feedback into your application that reacts based on the readiness state (such as increasing load if the application is ready), you may indirectly achieve autoscaling based on readiness state. This may require modifications to your application code or leveraging a more complex metrics pipeline.
