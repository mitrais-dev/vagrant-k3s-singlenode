# K3S Cluster

This vagrant will create one virtual machine for Kubernetes Control Plane. The default IP Address is `192.168.2.100` see details in `Vagrantfile`.

## Ingredient

- [Vagrant](https://www.vagrantup.com/downloads)
- [Kubernetes Command-Line Tool](https://kubernetes.io/docs/tasks/tools/)

## How to run

- Execute `vagrant up` to start the virtual machines. First time start will setup K3S cluster.
- Modify generated `k3s.yaml`, change the server IP Address to point to virtual machine.

  ```yaml
  - cluster:
      server: https://IP:6443
  ```

Test with kubectl using `k3s.yaml` as config:

```console
kubectl --kubeconfig k3s.yaml version
```

## Deploy Sample Appplication

Execute `kubectl --kubeconfig sample-deployment.yaml`.
The application can be accessed through `http://IP`.

## TIPS

If you are not familiar with `kubectl` command you can use [Octant](https://octant.dev) to view the cluster.
Execute `octant --kubeconfig k3s.yaml` and octant will be available in <http://127.0.0.1:7777>