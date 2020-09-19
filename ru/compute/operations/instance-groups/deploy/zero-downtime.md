# Обновление без простоя

Чтобы избежать недоступности вашего сервиса, можно обновлять группу виртуальных машин через создание дополнительных машин с новой конфигурацией. 
По мере добавления в группу машин с новой конфигурацией, машины со старой конфигурацией будут удаляться.

Для этого:

1. Опишите необходимый [шаблон](../../../concepts/instance-groups/instance-template.md) виртуальной машины.
1. Задайте [политику развертывания](../../../concepts/instance-groups/policies/deploy-policy.md) с ненулевым значением `max_expansion` — максимальным количеством дополнительно создаваемых машин.
1. Запустите [операцию обновления](../../../operations/instance-groups/update.md) группы.

Например, чтобы обновить группу по описанному алгоритму, добавляя и удаляя по одной виртуальной машине, в `deploy-policy` следует задать следующие параметры:

```
...
deploy-policy:
    max_unavailable = 0
    max_expansion = 1
    ...
...
```

Обновление группы будет выполняться следующим образом:

![Blue-green deployment](../../../../_assets/instance-groups/blue-green.gif "Zero-downtime deployment")