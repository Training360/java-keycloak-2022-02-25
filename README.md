# Keycloak

## Domain nevek beállítása

```shell
echo 192.168.70.80 keycloak.training >> C:\Windows\System32\drivers\etc\hosts
echo 192.168.70.80 employees.training >> C:\Windows\System32\drivers\etc\hosts
echo 192.168.70.80 employees-ui.training >> C:\Windows\System32\drivers\etc\hosts
```

## Keycloak indítása

```shell
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/keycloak-secret.yaml
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/keycloak-deployment.yaml
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/employees-ui-deployment.yaml
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/employees-deployment.yaml
```