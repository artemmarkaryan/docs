# Как осуществить маршутизацию трафика между двумя облачными сетями


## Описание сценария {#case-description}

Необходимо связать две VPC.

## Решение {#case-resolution}

Для решения этой задачи есть несколько решений:

Можем предложить несколько решений:

1. **Маршрутизация через интернет**: в каждой из подсетей создаётся по ВМ с внешним адресом, к подсетям привязывается таблицы маршрутизации, завязанные на эти внешние адреса.
2. **Создание VPN-туннеля из одной сети в другую** – потребуется в одной из подсетей ВМ с внешним адресом, где настраивается VPN-сервер. В другой подсети настраивается на ВМ с доступом в интернет подключение к этом серверу, после чего таблицы маршрутизации привязываются к этим подсетям через VPN-туннель. На маркетплейсе у нас есть готовые решения для [OpenVPN](../../../vpc/tutorials/openvpn.md) и [IPSec](../../../vpc/tutorials/ipsec/ipsec-vpn.md).
3. **Использование специальных ВМ-маршрутизаторов**: ряд образов позволяет создавать ВМ с несколькими интерфейсами, которые могут быть связаны с разными облачными сетями. Самым простым будет использовать NAT-инстанс с маркетплейса. В документации описан [сценарий использования такого образа](../../../vpc/tutorials/nat-instance.md) для организации доступа в интернет, вы можете его использовать как основу. Обратите внимание, что нужно будет добавить ВМ второй интерфейс с адресом в нужной подсети и указать в таблицах маршрутизации конкретные маршруты вместо дефолтного.
4. Если вы знакомы с **решениями от [CISCO](../../../vpc/tutorials/cisco.md) или [Mikrotik](../../../vpc/tutorials/mikrotik.md)**, можно использовать их виртуальные роутеры, их образы также доступны на маркетплейсе, однако они требуют лицензий для полноценной работы. На таких ВМ тоже можно создавать несколько сетевых интерфейсов, только конфигурировать их нужно самостоятельно.