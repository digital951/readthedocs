Test File (What does this do?)
=====

.. _Good-Examples:

Good Examples
------------

`Manually Started Redis Cluster <https://medium.com/geekculture/redis-cluster-on-kubernetes-c9839f1c14b6>`_

This cluster uses statefulsets and a script to start but has lots of good K8s concepts. 

.. code-block:: bash

   $ ./start-redis.sh

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']
