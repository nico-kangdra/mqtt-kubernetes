### Install MQTT with Helm

1. Add Helm Repo
   ```sh
   helm repo add k8s-at-home https://k8s-at-home.com/charts/
   helm repo update
   ```

2. Prepare `values.yml`

3. Install with helm command
   ```sh
   helm upgrade --install mosquitto k8s-at-home/mosquitto -f values.yml
   ```


### Expose TCP Ingress with Nginx-Ingress

1. Edit helm values and add this:
   ```sh
   tcp:
   "1883": default/mosquitto:1883
   ```

2. Then save and redeploy the helm release


### Install with NodePort
1. Edit the values.yml and change the service to NodePort

2. Reinstall with helm command
   ```sh
   helm upgrade --install mosquitto k8s-at-home/mosquitto -f values-nodeport.yml
   ```


### Install Horizontal Pod Autoscaler

1. 