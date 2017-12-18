# AndreyErmilov_infra

## Homework 5

### Основное задание

Конфигурация

```
Хост bastion, IP: 35.189.245.203, внутр. IP: 10.132.0.2
Хост: someinternalhost, внутр. IP: 10.132.0.3
```

Подключение к internalhost через ssh
``ssh -o ProxyCommand='ssh -W %h:%p appuser@35.189.245.203' appuser@10.132.0.3``

### Дополнительное задание

Нужно добавить в `~/.ssh/config` строки:
```
HOST bastion
    IdentityFile ~/.ssh/appuser
    User appuser
    HostName 35.189.245.203

HOST internalhost
    IdentityFile ~/.ssh/appuser
    User appuser
    HostName 10.132.0.3
    ProxyCommand ssh bastion -W %h:%p
```

Подключение
``ssh internalhost`` или ``ssh bastion``