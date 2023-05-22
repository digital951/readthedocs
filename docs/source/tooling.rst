K8s Tooling
=====

.. _k8s-tooling:

k9s
------------

`K9s Github Page <https://github.com/derailed/k9s>`_

`Download K9s Page <https://github.com/derailed/k9s/releases>`_

Kubernetes CLI To Manage Your Clusters In Style!

.. code-block:: bash

   $ ./k9s

Or for context specification


.. code-block:: bash

   $ ./k9s --context <MY-CONTEXT>
   
ytt
------------


`VMware currated ytt <https://carvel.dev/ytt/>`_

Template and patch as needed to easily make your configuration reusable and extensible. Works with your own and third-party YAML configuration. 

.. code-block:: bash

   $ ./ytt
   
imgpkg
------------

`VMware curated imgpkg <https://carvel.dev/imgpkg/>`_

Package, distribute, and relocate your Kubernetes configuration and dependent OCI images as one OCI artifact: a bundle. Consume bundles with confidence that their contents are unchanged after relocation.

.. code-block:: bash

   $ ./imgpkg
   
kapp
------------

`Manually Started Redis Cluster <https://carvel.dev/kapp/>`_

Deploy and view groups of Kubernetes resources as "applications". Apply changes safely and predictably, watching resources as they converge. 

.. code-block:: bash

   $ ./kapp
