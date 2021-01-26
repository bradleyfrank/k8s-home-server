# k8s-home-server

Home server based on k0s.

## Pre-tasks

```sh
ansible-galaxy collection install -r requirements.yml
```

## Post-tasks

```sh
cat ~/k0s-kube-config >> ~/.kube/config
```
