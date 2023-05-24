Terminal Configuration
=====

.. _Terminal-config:

Add the lines below to your .bashrc or .bashprofile

.. code-block:: bash

    # Add ~/bin to the PATH
    export PATH="$HOME/bin:$PATH"

    # Enable kubectl bash completion
    source <(kubectl completion bash)


NOTE: You may have to update FAPOLICY and/or SElinux to allow binary's to run from you home directory. 
~/bin is a easy place to drop kubectl, ytt and other tooling durring a proof of concept or demo.

