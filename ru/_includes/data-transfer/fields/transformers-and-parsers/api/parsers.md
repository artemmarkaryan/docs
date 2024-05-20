`parser` — правила конвертации, которые определяются одним из выбранных парсеров:

* `auditTrailsV1Parser` — парсер для логов сервиса [{{ at-name }}](../../../../../audit-trails/).

* `cloudLoggingParser` — парсер для логов сервиса [{{ cloud-logging-short-name }}](../../../../../logging/).

* `jsonParser` или `tskvParser` — парсеры JSON и TSKV, соответственно.

    Поля, задающие параметры их работы, одинаковы для обоих парсеров:

    * `dataSchema` — схема данных, представленная либо в виде JSON-объекта с описанием схемы, либо в виде списка полей:

        * `fields` — схема в виде JSON-объекта. Объект содержит в себе массив JSON-объектов, которые описывают отдельные колонки.

        * `jsonFields` — схема в виде списка JSON-полей.

    * `nullKeysAllowed` — задайте значение `true` для этого поля, чтобы разрешить значение `null` в ключевых колонках.

    * `addRestColumn` — задайте значение `true` для этого поля, чтобы поля, отсутствующие в схеме, попадали в колонку `_rest`.

    * `unescapeStringValues` — задайте значение `true` для этого поля, чтобы убрать кавычки из строковых переменных (если этого не сделать, значения строковых полей останутся без изменений).