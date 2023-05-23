Single TCP Connection
=====

In Kubernetes, how to make sure one pod only serve one connection


Situation
---------

I want to have a pool of serving pods (say I have 50 serving pods lying around). They will be exposed via a LoadBalancer Service.

I want to make sure that:

- each pod serves only one TCP connection and keep this connection alive until the client terminates it. Until the end of this pod's life, it will not receive any other TCP connections.
- Once the client terminates the connection, the pod cleans up and destroys it self.
- Another pod is spinned up to match the desired replica number. Since it's not currently serving any TCP connection, it can be chosen to serve the next TCP connection that goes into the LoadBalancer service.

Example
-------

Please see the text content for detailed example. 

Does anybody have any ideas how this can be solved on K8s?

.. _kubernetes: https://kubernetes.io/

| **kubernetes**
| **Share**
| **Improve this question**
| **Follow**
| asked Feb 24, 2020 at 17:49
| **Tran Triet**
| 1,22711 gold badge1616 silver badges3434 bronze badges
| Add a comment

Answers
-------

Sorted by: Highest score (default)

1. Andreas Wederbrand's suggested solution:

   Please see the text content for the detailed solution and discussion. 

   .. _Andreas Wederbrand: https://stackoverflow.com/users/56841/andreas-wederbrand

2. Vikram Hosakote's suggestion about using k8s' sessionAffinity:

   Please see the text content for the detailed suggestion and discussion. 

   .. _Vikram Hosakote: https://stackoverflow.com/users/683282/vikram-hosakote

3. Arghya Sadhu's idea of using serverless technology on top of kubernetes:

   Please see the text content for the detailed idea and discussion. 

   .. _Arghya Sadhu: https://stackoverflow.com/users/2542847/arghya-sadhu

4. Unnamed user's recommendation to use StatefulSet and Headless Service:

   Please see the text content for the detailed recommendation. 
