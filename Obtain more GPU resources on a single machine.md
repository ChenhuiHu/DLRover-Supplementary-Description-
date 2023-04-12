# Obtain more GPU resources on a single machine

1. Add the NVIDIA Helm repository:

   ```bash
   $ helm repo add nvdp https://nvidia.github.io/k8s-device-plugin
   ```

   This will add a repository named `nvdp` to your Helm configuration.

2. Update the Helm repository index:

   ```bash
   $ helm repo update
   ```

   Update the repository index to ensure you have the latest chart versions and information.

3. Verify if the `nvidia-device-plugin` chart is in the repository:

   ```bash
   $ helm search repo nvdp
   ```

   This will display all Helm charts in the `nvdp` repository, including `nvidia-device-plugin`.

4. Install or upgrade the `nvidia-device-plugin` Helm chart:

   Install:

   ```bash
   $ helm install nvdp nvdp/nvidia-device-plugin \
       --version=0.13.0 \
       --namespace nvidia-device-plugin \
       --create-namespace \
       --set-file config.map.config=./dlrover/go/operator/config/gpu/nvidia-device-plugin-gpu-shared.yaml
   ```

   Or upgrade (if already installed):

   ```bash
   $ helm upgrade -i nvdp nvdp/nvidia-device-plugin \
       --version=0.13.0 \
       --namespace nvidia-device-plugin \
       --create-namespace \
       --set-file config.map.config=./dlrover/go/operator/config/gpu/nvidia-device-plugin-gpu-shared.yaml
   ```

