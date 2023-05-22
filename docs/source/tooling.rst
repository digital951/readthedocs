K8s Tooling
=====

.. _k8s-tooling:

k9s
------------

Here is the `K9s Github Page <https://github.com/derailed/k9s>`_

`Download K9s Page <https://github.com/derailed/k9s/releases>`_

Kubernetes CLI To Manage Your Clusters In Style!

.. code-block:: bash

   $ ./k9s

Or for context specification


.. code-block:: bash

   $ ./k9s --context <MY-CONTEXT>
   
ytt
------------


`VMware currated ytt<https://carvel.dev/ytt/>`_

Template and patch as needed to easily make your configuration reusable and extensible. Works with your own and third-party YAML configuration. 

.. code-block:: bash

   $ ./ytt
   
imgpkg
------------

`Manually Started Redis Cluster <https://medium.com/geekculture/redis-cluster-on-kubernetes-c9839f1c14b6>`_

This cluster uses statefulsets and a script to start but has lots of good K8s concepts. 

.. code-block:: bash

   $ ./start-redis.sh
   
kapp
------------

`Manually Started Redis Cluster <https://medium.com/geekculture/redis-cluster-on-kubernetes-c9839f1c14b6>`_

This cluster uses statefulsets and a script to start but has lots of good K8s concepts. 

.. code-block:: bash

   $ ./start-redis.sh
