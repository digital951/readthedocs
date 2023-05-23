TKGm
=====

   
1. **Prerequisites:**
   
   * VMware vCenter Server (7.0 or later) and ESXi hosts (6.7 or later).
   * Install and configure VMware vSphere with Tanzu.
   * Install and configure NSX-T (3.0 or later) for networking.
   * Configure a Content Library in vSphere for TKG images.
   * Install and configure Docker (19.03 or later) on your local machine.
   * Download the TKG CLI (tanzu CLI) from VMware's official website.

2. **Install the TKG CLI (tanzu CLI) on your local machine:**

   * Extract and copy the CLI binary to your system's PATH.
   * Run ``tanzu version`` to verify the installation.

3. **Configure the CLI with vSphere:**

   * Create a configuration file (e.g., ``vsphere-config.yaml``) with your vSphere credentials and other details.
   * Run ``tanzu login --config-file vsphere-config.yaml`` to authenticate with vSphere.

4. **Create a TKG Management Cluster:**

   * Create a cluster configuration file (e.g., ``tkg-management-cluster.yaml``) with the desired settings for the management cluster.
   * Run ``tanzu cluster create --config-file tkg-management-cluster.yaml --tkr-version <tkr-version>`` to deploy the TKG Management Cluster.

5. **Set the context to the TKG Management Cluster:**

   * Run ``tanzu context set <management-cluster-name>`` to switch the context to the management cluster.

6. **Deploy TKG Workload Clusters (optional):**

   * Create a workload cluster configuration file (e.g., ``tkg-workload-cluster.yaml``) with the desired settings for the workload cluster.
   * Run ``tanzu cluster create --config-file tkg-workload-cluster.yaml --tkr-version <tkr-version>`` to deploy the TKG Workload Cluster.

For more detailed instructions, refer to the official `VMware Tanzu Kubernetes Grid documentation <https://docs.vmware.com/en/VMware-Tanzu-Kubernetes-Grid/index.html>`_.
