# Как начать работать c сервисными аккаунтами

Сервис {{ iam-short-name }} позволяет вам создавать [_сервисные аккаунты_](concepts/users/service-accounts.md) — дополнительные аккаунты, с помощью которых программы могут выполнять операции в {{ yandex-cloud }}. Сервисные аккаунты бесплатны и позволяют гибко управлять доступами ваших программ. Подробнее в разделе [{#T}](concepts/users/service-accounts.md).

Эта инструкция для [владельцев облака](../resource-manager/concepts/resources-hierarchy.md#owner) и пользователей с ролью [администратора](concepts/access-control/roles.md#admin) на облако или каталог. Пользователи с ролью [`editor`](concepts/access-control/roles.md#editor) тоже могут создавать сервисные аккаунты, но не могут назначать роли, поэтому не смогут разрешить сервисному аккаунту выполнение операций в {{ yandex-cloud }}.

Вы научитесь:

* [Создавать сервисные аккаунты и назначать им роли](#create-sa).
* [Выполнять операции в CLI](#run-operation-from-sa).
* [Удалять сервисные аккаунты](#delete-sa).

## Перед началом {#before-you-begin}

1. Если вы еще не зарегистрированы в {{ yandex-cloud }}, перейдите в [консоль управления](https://console.cloud.yandex.ru).
1. [На странице биллинга](https://console.cloud.yandex.ru/billing) убедитесь, что у вас подключен [платежный аккаунт](../billing/concepts/billing-account.md) и он находится в статусе `ACTIVE` или `TRIAL_ACTIVE`. Если платежного аккаунта нет, [создайте его](../billing/quickstart/index.md#create_billing_account).

## Создайте сервисный аккаунт {#create-sa}

Чтобы создать сервисный аккаунт и назначить ему роли:

{% include [create-sa-via-console](../_includes/iam/create-sa-via-console.md) %}

## Настройте CLI для работы от имени сервисного аккаунта {#run-operation-from-sa}

От имени сервисного аккаунта вы можете выполнять операции через API, CLI и другие инструменты, которые поддерживают аутентификацию с сервисным аккаунтом. В консоль управления войти с помощью сервисного аккаунта нельзя.

{% include [cli-set-sa-profile](../_includes/cli-set-sa-profile.md) %}

Теперь вы можете выполнять операции от имени сервисного аккаунта, например посмотреть список каталогов, доступных этому аккаунту:

```
yc resource-manager folder list
```

## Удалите сервисный аккаунт {#delete-sa}

Если сервисный аккаунт больше не нужен, удалите его:

{% include [delete-sa-via-console](../_includes/iam/delete-sa-via-console.md) %}

## Что дальше {#what-is-next}

* [Пошаговые инструкции](operations/index.md) помогут вам решить конкретные задачи, возникающие при использовании {{ iam-name }}.
* [Подробнее про сервисные аккаунты](concepts/users/service-accounts.md) написано в концепциях.
* Посмотрите [рекомендации по безопасному использованию сервисных аккаунтов](best-practices/using-iam-securely.md#use-sa).