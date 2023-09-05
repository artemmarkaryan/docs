# Удаление облака



## Описание задачи {#case-description}

Возникла необходимость удалить облако.

## Решение {#case-resolution}

{% note info %}

Для удаления облака обязательна роль `resource-manager.clouds.owner` на это облако.

{% endnote %}

Для удаления облака в консоли управления нужно:

1. Выбрать облако в списке;
2. Нажать на кнопку **···** и выбрать **Удалить**;
3. Выбрать срок, после которого облако будет удалено — один из возможных периодов или опция **Удалить сейчас**. Срок удаления Облака по умолчанию — 7 дней.
4. Нажать **Удалить**.

После этого ресурсы будут остановлены и облако перейдет в статус ожидания удаления `PENDING_DELETION`. Удаление облака, находящегося в статусе `PENDING_DELETION`, можно отменить.

После завершения периода ожидания Облако переходит в статус `DELETING`. В этом статусе происходит процесс необратимого удаления, занимающий до 72 часов.

Подробнее пишем в [документации](https://cloud.yandex.ru/docs/resource-manager/operations/cloud/delete).