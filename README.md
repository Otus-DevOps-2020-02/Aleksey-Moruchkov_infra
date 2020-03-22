# Aleksey-Moruchkov_infra
Aleksey-Moruchkov Infra repository

# ДЗ "Знакомство с облачной инфраструктурой"

bastion_IP = 34.76.61.255
someinternalhost_IP = 10.132.0.3

## Дополнительное задание

Как подключиться с локальной машины с помощью команды вида `ssh someinternalhost`:

- На локальной машине добавляем в `~/.ssh/config` следующее содержимое:

```
Host bastion
  HostName     34.76.61.255
  User         master
  IdentityFile ~/.ssh/id_rsa
  ForwardAgent yes

Host someinternalhost
  HostName     10.132.0.3
  User         master
  ProxyJump    bastion
```
- Теперь для подключения к **someinternalhost** в приватной сети GCP проекта можно использовать команду
```
ssh someinternalhost
```
