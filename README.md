# Keycloak

## Domain nevek beállítása

```shell
echo 192.168.70.80 keycloak.training >> C:\Windows\System32\drivers\etc\hosts
echo 192.168.70.80 employees.training >> C:\Windows\System32\drivers\etc\hosts
echo 192.168.70.80 employees-ui.training >> C:\Windows\System32\drivers\etc\hosts
```

## Keycloak indítása

```shell
# Keycloak secret
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/keycloak-secret.yaml
# Keycloak
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/keycloak-deployment.yaml
# Employees UI
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/employees-ui-deployment.yaml
# Employees
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/employees-deployment.yaml
```

A Keycloak elérhető a `http://keycloak.training:30010` címen.

A frontend címe: `http://employees-ui.training:30011`

A backend címe: `http://employees.training:30012`

## Realm létrehozás

Név: `employees`

## Client létrehozása

* Id: `employees-ui`
* URL: `http://employees-ui.training:30011`
* Admin URL törlése

## Felhasználó létrehozás

* `johndoe`, `johndoe@localhost`, e-mail ellenőrizve
* Jelszó beállítás, nem temporary jelszó

## Szerepkör létrehozás

* `employees_user`
* Felhasználónak adjuk oda a szerepkört

## Token lekérése

```
curl -s --data "grant_type=password&scope=openid&client_id=employees-ui&username=johndoe&password=johndoe" http://keycloak.training:30010/auth/realms/employees/protocol/openid-connect/token
```

## Token felhasználása

```
curl -s --header "Authorization: bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJrazBUTFI3RUZ5clJseFViaENtelV3UlpVSm5sQUNoTjNGMGRrYkRFVVljIn0.eyJleHAiOjE2NDU3OTQxODksImlhdCI6MTY0NTc5Mzg4OSwianRpIjoiNjNlMGZhMTgtNjJkMi00NDMxLTg1MjYtNmVkMTg5ZGVkNTliIiwiaXNzIjoiaHR0cDovL2tleWNsb2FrLnRyYWluaW5nOjMwMDEwL2F1dGgvcmVhbG1zL2VtcGxveWVlcyIsImF1ZCI6ImFjY291bnQiLCJzdWIiOiI4Y2YzNjE2MC02NWIyLTQ0MjMtOTM4OS0xODBlYWYyZmViOTciLCJ0eXAiOiJCZWFyZXIiLCJhenAiOiJlbXBsb3llZXMtdWkiLCJzZXNzaW9uX3N0YXRlIjoiNmYwMzQ3MjQtMGIzZi00MDhkLWI1N2QtZmQxZWVhODdjNjhjIiwiYWNyIjoiMSIsImFsbG93ZWQtb3JpZ2lucyI6WyJodHRwOi8vZW1wbG95ZWVzLXVpLnRyYWluaW5nOjMwMDExIl0sInJlYWxtX2FjY2VzcyI6eyJyb2xlcyI6WyJkZWZhdWx0LXJvbGVzLWVtcGxveWVlcyIsIm9mZmxpbmVfYWNjZXNzIiwidW1hX2F1dGhvcml6YXRpb24iLCJlbXBsb3llZXNfdXNlciJdfSwicmVzb3VyY2VfYWNjZXNzIjp7ImFjY291bnQiOnsicm9sZXMiOlsibWFuYWdlLWFjY291bnQiLCJtYW5hZ2UtYWNjb3VudC1saW5rcyIsInZpZXctcHJvZmlsZSJdfX0sInNjb3BlIjoib3BlbmlkIHByb2ZpbGUgZW1haWwiLCJzaWQiOiI2ZjAzNDcyNC0wYjNmLTQwOGQtYjU3ZC1mZDFlZWE4N2M2OGMiLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwibmFtZSI6IkpvaG4gRG9lIiwicHJlZmVycmVkX3VzZXJuYW1lIjoiam9obmRvZSIsImdpdmVuX25hbWUiOiJKb2huIiwiZmFtaWx5X25hbWUiOiJEb2UiLCJlbWFpbCI6ImpvaG5kb2VAbG9jYWxob3N0In0.F7kzj4oepKl8z7skO2IxVUIh1JhmwFsKSj2spzBWqFXBwPrWCkIf5TxIWqN8MpMpZ89Y-xTHJ8iCE6esq0gkbfKiEm7bKLwOwbns8_ZdKky2F7hG5HJXxAfxWRc4_7Qo02wSdrXUDxbbqHZc9JwamDxTe0l3i4BaESEDFwx3_FMUKXza_ytJsk4Jnieo1YXAsOETFdT3Q8UiCNHzElyC93YfUg3wWootks3U93nUPiYWKPDggYcGDAATJnXPLkMqA_5XTRIDJeM3yj0hNw0KOUKMoJfUPR6Pm2PFlunriOexB4aTtWxERvZcu_koEDkUMonTi-pW7S-mQSof0k7w1g" http://employees.training:30012/api/employees
```

# Bejelentkezés e-maillel

# Remember me

# Saját regisztráció

# Account console

# Törölni saját magát

# Password policy

# User locale

# Saját attribútum

# Consent

Adatok jóváhagyása

# Terms and conditions

# E-mailek kezelése

```shell
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/mailhog-deployment.yaml
```

Elérhető `http://192.168.70.80:30013/` címen

# GitHub

# OpenLDAP

```shell
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/openldap-secret.yaml
kubectl apply -f https://raw.githubusercontent.com/Training360/java-keycloak-2022-02-25/master/deployments/openldap-deployment.yaml
```

```
Vendor: other
User object class: inetOrgPerson
Connection url: ldap://openldap:1389
Users DN: ou=users,dc=example,dc=org
Bind DN: cn=admin,dc=example,dc=org
Bind credential: admin
```

# DB hozzáférés

# Events

* Log
* DB

# REST API

https://www.keycloak.org/docs-api/15.0/rest-api/

```shell
curl -s --data "grant_type=password&scope=openid&client_id=admin-cli&username=root&password=root" http://keycloak.training:30010/auth/realms/master/protocol/openid-connect/token
curl --header "Accept: application/json" --header "Authorization: bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJWbXBfVGNPWWctUTBnbHV3VUFPVXlGQW4wekhDTHBlWi13Y2QxNHRfdGpnIn0.eyJleHAiOjE2NDU3MTA5MTMsImlhdCI6MTY0NTcxMDg1MywianRpIjoiMjE3NjkzYWQtNzQzYi00OWUxLTk3YzctMmUzOGIwZmZhYWRjIiwiaXNzIjoiaHR0cDovL2tleWNsb2FrLnRyYWluaW5nOjMwMDEwL2F1dGgvcmVhbG1zL21hc3RlciIsInN1YiI6IjZmNTQ0YzAwLTVkMDMtNDRlOC04MTQzLTAyY2Q0NzA5MTFkOCIsInR5cCI6IkJlYXJlciIsImF6cCI6ImFkbWluLWNsaSIsInNlc3Npb25fc3RhdGUiOiIzNTAyODRkMy0wMmM5LTQ5ZGMtYWU2Ny03NTEwYmU1OWM4NmEiLCJhY3IiOiIxIiwic2NvcGUiOiJvcGVuaWQgZW1haWwgcHJvZmlsZSIsInNpZCI6IjM1MDI4NGQzLTAyYzktNDlkYy1hZTY3LTc1MTBiZTU5Yzg2YSIsImVtYWlsX3ZlcmlmaWVkIjpmYWxzZSwicHJlZmVycmVkX3VzZXJuYW1lIjoicm9vdCIsImVtYWlsIjoia2V5Y2xvYWtAbG9jYWxob3N0In0.CtipTgWP_RzhsYdVD2IHKZ4OyDaPu_YTtFVl5hhk6QBIGWil_6oQ0suSsLifVBjfcqd5euO5zukGnUm_z00MpsdLndu6ak84GBL_WSeWT6beGiDxH6OKqhZjOAo7tY4c2hblOJ5aOYb5zUfdMD7mVqHQslL4wJVBaJnuSeSLc2-V4H3ecUszFGSCbHMdf5Ejo3ovxNd-nxbaNKwAKAYwVuwvLlY9St9byesfPVTelnzXtdxuCgEmB9p2NFsZEX7iumfQ_wWvU2rFQcF_ekme2eCg5ClwYQs219uDRDTTN1sww0CkJ7N800XqiIl8mXobSWIBDO9oZbTMfUtxDLm9Pg" http://keycloak.training:30010/auth/admin/realms/employees/users
```

Postmannel

# Admin CLI

```shell
kubectl exec -it pod/keycloak-7b5fb99f-zpbj6 -- /opt/jboss/keycloak/bin/kcadm.sh config credentials --server http://127.0.0.1:8080/auth --realm master get users --user root

kubectl exec -it pod/keycloak-7b5fb99f-zpbj6 -- /opt/jboss/keycloak/bin/kcadm.sh get users -r employees
kubectl exec -it pod/keycloak-7b5fb99f-zpbj6 -- /opt/jboss/keycloak/bin/kcadm.sh get events -r employees

kubectl exec -it pod/keycloak-7b5fb99f-zpbj6 -- /opt/jboss/keycloak/bin/kcadm.sh create users -s username=johnsmith -s enabled=true -r employees
kubectl exec -it pod/keycloak-7b5fb99f-zpbj6 -- /opt/jboss/keycloak/bin/kcadm.sh set-password --username johnsmith --new-password johnsmith  -r employees
```