# nfs_dynamic_pv_provisioning
README: NFS Dynamic PV Provisioning

This repository contains configurations for setting up dynamic storage provisioning using NFS (Network File System) in Kubernetes.

## Files

- `nfs_class.yaml`: This file defines the StorageClass for NFS dynamic provisioning. The StorageClass specifies the parameters and settings for creating PersistentVolumes dynamically using NFS as the storage backend.

- `nfs_deployment.yaml`: Deploying the NFS client provisioner is done using this file. The NFS client provisioner is responsible for dynamically provisioning PersistentVolumes based on the PersistentVolumeClaim (PVC) requests.

- `nfs_dynamic_provisioning_note.yaml`: This file provides additional notes and considerations for NFS dynamic provisioning. It contains important information, tips, and best practices related to the setup and usage of NFS dynamic provisioning in Kubernetes.

- `nfs_rbac.yaml`: The RBAC (Role-Based Access Control) settings required for the NFS client provisioner are defined in this file. RBAC ensures that only authorized entities have the necessary permissions to create and manage PersistentVolumes.

- `pvc-nfs.yaml`: This file serves as an example PersistentVolumeClaim (PVC) configuration for requesting storage using NFS dynamic provisioning. It demonstrates how to define a PVC that will trigger the dynamic creation of a PersistentVolume with NFS as the storage backend.

## Usage

To set up NFS dynamic PV provisioning in your Kubernetes cluster, follow these steps:

1. Apply the `nfs_rbac.yaml` file to create the necessary RBAC roles and role bindings. These RBAC settings allow the NFS client provisioner to perform the required operations for dynamic PV provisioning:

   ```bash
   kubectl apply -f nfs_rbac.yaml
   ```

2. Apply the `nfs_deployment.yaml` file to deploy the NFS client provisioner in your cluster. The NFS client provisioner will listen for PVC requests and create the necessary PVs dynamically:

   ```bash
   kubectl apply -f nfs_deployment.yaml
   ```

3. Apply the `nfs_class.yaml` file to configure the StorageClass for NFS dynamic provisioning. The StorageClass defines the parameters and settings for creating PVs backed by NFS:

   ```bash
   kubectl apply -f nfs_class.yaml
   ```

4. Use the `pvc-nfs.yaml` file as a template to create your own PVCs for dynamic provisioning. Adjust the storage size, access modes, and other parameters as needed. PVCs will trigger the NFS dynamic provisioning process:

   ```bash
   kubectl apply -f pvc-nfs.yaml
   ```

Make sure you have the necessary permissions and access to the NFS server before proceeding with the setup.

For more details and specific configurations, refer to the individual files in this repository.

## License

This project is licensed under the [MIT License](LICENSE). You are free to modify and use the configurations according to your needs.

## Acknowledgements

This setup is based on the work and contributions from the Kubernetes community and the NFS client provisioner project. We acknowledge and appreciate their efforts in enabling NFS dynamic PV provisioning in Kubernetes.
