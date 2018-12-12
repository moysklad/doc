## Документ Счёт поставщика
### Счета поставщиков 
Средствами JSON API можно создавать и обновлять сведения о Счёте поставщика, запрашивать списки Счетов и сведения по отдельным Счетам Поставщиков. Позициями Счетов можно управлять как в составе отдельного Счёта, так и отдельно - с помощью специальных ресурсов для управления позициями Счёта. Кодом сущности для Счёта поставщика в составе JSON API является ключевое слово **invoicein**. Больше о Счетах Поставщиков и работе с ними в основном интерфейсе вы можете прочитать в нашей службе поддержки по [этой ссылке](https://support.moysklad.ru/hc/ru/articles/203053506-%D0%A1%D1%87%D0%B5%D1%82%D0%B0-%D0%BF%D0%BE%D1%81%D1%82%D0%B0%D0%B2%D1%89%D0%B8%D0%BA%D0%BE%D0%B2).

#### Атрибуты сущности
+ **meta** - [Метаданные](/api/remap/1.2/doc/index.html#header-метаданные) о Счёте поставщика
+ **id** - ID в формате UUID `Только для чтения`
+ **accountId** - ID учетной записи `Только для чтения`
+ **syncId** - ID синхронизации. После заполнения недоступен для изменения.
+ **updated** - Момент последнего обновления сущности `Только для чтения`
+ **deleted** - Момент последнего удаления сущности `Только для чтения`
+ **name** - номер Счёта поставщика
+ **description** - Комментарий Счёта поставщика
+ **externalCode** - Внешний код Счёта поставщика
+ **moment** - Дата Счёта
+ **applicable** - Отметка о проведении
+ **vatEnabled** - Учитывается ли НДС
+ **vatIncluded** - Включен ли НДС в цену
+ **sum** - Сумма Счёта в установленной валюте `Только для чтения`
+ **rate** - Валюта
+ **owner** - Ссылка на Владельца (Сотрудника) в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **shared** - Общий доступ
+ **group** - Отдел сотрудника в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **organization** - Ссылка на ваше юрлицо в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные) `Необходимое`
+ **agent** - Ссылка на контрагента в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные) `Необходимое`
+ **store** - Ссылка на склад в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **contract** - Ссылка на договор в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **state** - Статус Счёта в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **organizationAccount** - Ссылка на счёт вашего юрлица в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **agentAccount** - Ссылка на счёт контрагента в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **attributes** - Коллекция доп. полей в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
<br>Поля при expand'е:</br>
  - **name** - номер документа
  - **moment** - дата печати
  - **href** - ссылка на файл печатной формы
  - **fileName** - название файла печатной формы
  - **updated** - дата последнего изменения
+ **created** - Дата создания `Только для чтения`
+ **vatSum** - Сумма НДС `Только для чтения`
+ **positions** - Ссылка на позиции в Счёте в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **paymentPlannedMoment** - Планируемая дата оплаты
+ **payedSum** - Сумма входящих платежей по Счёту поставщика `Только для чтения`
+ **shippedSum** - Сумма отгруженного `Только для чтения`
+ **project** - Ссылка на проект в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **incomingNumber** - Входящий номер
+ **incomingDate** - Входящая дата
#### Связи с другими документами
+ **payments** - Массив ссылок на связанные операции в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные) `Только для чтения`
+ **purchaseOrder** - Ссылка на связанный заказ поставщику в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **supplies** - Ссылки на связанные приёмки в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)

#### Позиции Счёта поставщика
Позиции Счёта - это список товаров/услуг/модификаций/серий.
Объект позиции Счёта содержит следующие поля:
+ **id** - ID товара в формате UUID `Только для чтения`
+ **accountId** - ID учетной записи `Только для чтения`
+ **quantity** - Количество товаров/услуг данного вида в позиции. Если позиция - товар, у которого включен учёт по серийным номерам, то значение в этом поле всегда будет равно количеству серийных номеров для данной позиции в документе.
+ **price** - Цена товара/услуги в копейках
+ **discount** - Процент скидки или наценки. Наценка указывается отрицательным числом, т.е. -10 создаст наценку в 10%
+ **vat** - НДС, которым облагается текущая позиция
+ **assortment** - Ссылка на товар/услугу/серию/модификацию, которую представляет собой позиция, в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **pack** - Упаковка товара

С позициями можно работать с помощью специальных ресурсов для управления позициями Счёта,
а также в составе отдельного Счёта поставщика. При работе в составе отдельного Счёта поставщика,
вы можете отправлять запросы на создание отдельного Счёта поставщика с включенным в тело запроса
массивом позиций Счёта. Если количество позиций превышает максимально допустимое, то для
дальнейшего пополнения позиций нужно будет работать со специальным ресурсом "Позиции Счёта поставщика".
Также, при работе в составе отдельного Счёта поставщика, можно отправлять запросы на обновление списка позиций
с включенным в тело запроса массивом позиций Счёта. При этом важно помнить, что коллекция позиций будет
восприниматься как "все позиции Счёта" и полностью заменит уже существующую коллекцию при обновлении объекта - лишние
позиции будут удалены, новые добавлены, существующие - изменены.

<!-- include(rate.apib) -->

О работе с доп. полями Счетов поставщиков можно прочитать [здесь](/api/remap/1.2/doc/index.html#header-работа-с-дополнительными-полями)


### Получить Счета поставщиков 
Запрос всех Счетов поставщиков на данной учётной записи.
Результат: Объект JSON, включающий в себя поля:
- **meta** [Метаданные](/api/remap/1.2/doc/index.html#header-метаданные) о выдаче,
- **context** - [Метаданные](/api/remap/1.2/doc/index.html#header-метаданные) о сотруднике, выполнившем запрос.
- **rows** - Массив JSON объектов, представляющих собой Счета поставщиков.
+ Parameters
  + limit: 1000 (optional, enum[number])
  Максимальное количество сущностей для извлечения.
  <p>
    <code>Допустимые значения 1 - 1000</code>
  </p>
      + Default: `1000`
  + offset: 40 (optional, number)
    Отступ в выдаваемом списке сущностей
      + Default: `0`

  + search: `0001` (optional, string)
    URL Параметр для поиска по имени документа.
    Фильтр документов по указанной поисковой строке. Фильтрация происходит по
    полю name.

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка Счетов поставщиков.
  + Body
        <!-- include(body/invoice_in/get_list.json) -->

### Создать Счёт поставщика 
Запрос на создание нового Счёта поставщика.
Обязательные для создания поля:
+ **name** - номер Счёта поставщика
+ **organization** - Ссылка на ваше юрлицо в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **agent** - Ссылка на контрагента (поставщика) в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ Request Пример (application/json)
Пример создания нового Счёта с телом запроса, содержащим только необходимые поля.
  + Body
        <!-- include(body/invoice_in/post_short_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/post_short_response.json) -->

+ Request Пример 2 (application/json)
Пример создания нового Счёта с более насыщенным телом запроса.
  + Body
        <!-- include(body/invoice_in/post_long_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/post_long_response.json) -->

+ Request Пример с доп. полями (application/json)
Пример запроса на создание Счёта поставщика с доп. полями.
  + Body
        <!-- include(body/invoice_in/post_with_attributes_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/post_with_attributes_response.json) -->

+ Request Пример с позициями (application/json)
Пример запроса на создание Счёта поставщика с позициями в теле запроса.
  + Body
        <!-- include(body/invoice_in/post_with_positions_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданного Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/post_with_positions_response.json) -->

### Массовое создание и обновление Счётов поставщика 
[Массовое создание и обновление](/api/remap/1.2/doc/index.html#header-создание-и-обновление-нескольких-объектов) Счётов поставщика.
В теле запроса нужно передать массив, содержащий JSON представления Счётов поставщика, которые вы хотите создать или обновить.
Обновляемые Счёта поставщика должны содержать идентификатор в виде метаданных.

+ Request Пример (application/json)
Пример создания и обновления нескольких Счётов поставщика
  + Body
        <!-- include(body/invoice_in/post_massive_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - массив JSON представлений созданных и обновленных Счётов поставщика.
  + Body
        <!-- include(body/invoice_in/post_massive_response.json) -->

### Удалить Счёт поставщика 
+ Parameters
  + id: `7944ef04-f831-11e5-7a69-971500188b19` (required, string) - id Счёта поставщика

Запрос на удаление Счёта поставщика с указанным id.

+ Response 200 (application/json)
Успешное удаление Счёта поставщика.

### Метаданные Счетов поставщиков 
#### Метаданные Счетов поставщиков 
Запрос на получение метаданных Счетов поставщиков. Результат - объект JSON, включающий в себя:
+ **meta** - Ссылка на метаданные Счетов поставщиков
+ **attributes** - Массив объектов доп. полей Счетов поставщиков в формате [Метаданных](/api/remap/1.2/doc/index.html#header-метаданные)
+ **states** - Массив статусов Счетов поставщиков
+ **createShared** - создавать новые Счета поставщиков с меткой "Общий"

Структура отдельного объекта, представляющего доп. поле подробно описана в разделе [Работа с дополнительными полями](/api/remap/1.2/doc/index.html#header-работа-с-дополнительными-полями).

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление доп. полей Счетов поставщиков.
  + Body
        <!-- include(body/invoice_in/metadata.json) -->

### Отдельное доп. поле 
+ Parameters
  + id: `7944ef04-f831-11e5-7a69-971500188b19` (required, string) - id Доп. поля
#### Отдельное доп. поле 
Запрос на получение информации по отдельному дополнительному полю.
+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельного доп. поля.
  + Body
        <!-- include(body/invoice_in/metadata_by_id.json) -->

### Шаблон счёта поставщика 
#### Шаблон счёта поставщика 
Запрос на получение предзаполненого стандартными значениями шаблона счёта поставщика без связи с каким-либо документом.

+ Request Пустое тело запроса (application/json)

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление предзаполненного счёта поставщика.
  + Body
        <!-- include(body/invoice_in/new_empty.json) -->

### Шаблон счёта поставщика на основе 
Запрос на получение предзаполненного счёта поставщика на основе заказа поставщику или приёмки.
В результате запроса, будет создан предзаполненный шаблон счёта поставщика на основе переданного
документа.
+ Request заказ поставщику (application/json)
Запрос на создание счёта поставщика на основе заказа поставщику.
  + Body
        <!-- include(body/invoice_in/new_order_request.json) -->
+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление предзаполненного счёта поставщика.
  + Body
        <!-- include(body/invoice_in/new_order_response.json) -->

+ Request приемка (application/json)
Запрос на создание счёта поставщика на основе приемки.
  + Body
        <!-- include(body/invoice_in/new_supply_request.json) -->
+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление предзаполненного счёта поставщика.
  + Body
        <!-- include(body/invoice_in/new_supply_response.json) -->


### Счёт поставщика 
+ Parameters
  + id: `7944ef04-f831-11e5-7a69-971500188b19` (required, string) - id Счёта поставщика
  
### Получить Счёт поставщика 
Запрос на получение отдельного Счёта поставщика с указанным id.
+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/get_by_id.json) -->

### Изменить Счёт поставщика 
Запрос на обновление Счета поставщика с указанным id.
В теле запроса можно указать только те поля, которые необходимо изменить у Счёта поставщика, кроме тех, что
помечены `Только для чтения` в описании [атрибутов Счёта поставщика](#документ-счёт-поставщика-счета-поставщиков).
При обновлении полей **organization** и **agent** нужно также обновить поля **organizationAccount** и
**agentAccount** соответственно, иначе произойдёт ошибка.

+ Request Пример (application/json)
Пример запроса на обновление отдельного Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/put_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновлённого Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/put_response.json) -->

+ Request Пример с доп. полями (application/json)
Пример запроса на изменение Счёта поставщика с дополнительными полями.
  + Body
        <!-- include(body/invoice_in/put_with_attributes_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновлённого Счёта поставщика.
  + Body
       <!-- include(body/invoice_in/put_with_attributes_response.json) -->

+ Request Пример с позициями (application/json)
Пример запроса на обновление Счёта поставщика с позициями в теле запроса.
  + Body
        <!-- include(body/invoice_in/put_with_positions_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновлённого Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/put_with_positions_response.json) -->

### Позиции Счёта поставщика 
Отдельный ресурс для управления позициями Счёта поставщика. С его помощью вы можете управлять позициями большого документа, количество строк в котором превышает лимит на количество строк, сохраняемых вместе с документом. Этот лимит равен 100. Более подробно о лимитах на количество строк документа и работе с большими документами можно прочитать [тут](/api/remap/1.2/doc/index.html#header-работа-с-позициями-документов).
+ Parameters
  + id: `7944ef04-f831-11e5-7a69-971500188b19` (required, string) - id Счёта поставщика
  
### Получить позиции Счёта поставщика 
Запрос на получение списка всех позиций данного Счёта поставщика.
- **meta** [Метаданные](/api/remap/1.2/doc/index.html#header-метаданные) о выдаче,
- **context** - [Метаданные](/api/remap/1.2/doc/index.html#header-метаданные) о сотруднике, выполнившем запрос.
- **rows** - Массив JSON объектов, представляющих собой позиции Счёта поставщика.

+ Parameters
  + limit: 1000 (optional, enum[number])
  Максимальное количество сущностей для извлечения.
  <p>
    <code>Допустимые значения 1 - 1000</code>
  </p>
      + Default: `1000`
  + offset: 40 (optional, number)
    Отступ в выдаваемом списке сущностей
      + Default: `0`

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление списка позиций отдельного Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/get_positions_list.json) -->
        
### Добавить позицию в Счёт поставщика 
Запрос на создание новой позиции в Счёте поставщика.
Для успешного создания необходимо в теле запроса указать следующие поля:
+ **assortment** - Ссылка на товар/услугу/серию/модификацию, которую представляет собой позиция.
Также можно указать поле с именем **service**, **consignment**, **variant** в соответствии с тем,
чем является указанная позиция. Подробнее об этом поле можно прочитать в описании [позиции Счёта](#header-позиции-счёта-поставщика)
+ **quantity** - Количество указанной позиции. Должно быть положительным, иначе возникнет ошибка.


+ Request Пример (application/json)
Пример создания позиции в Счёте поставщика.
  + Body
      <!-- include(body/invoice_in/post_position_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление созданной позиции отдельного Счёте поставщика.
  + Body
        <!-- include(body/invoice_in/post_position_response.json) -->


### Позиция Счёта поставщика 
Отдельная позиция Счёта поставщика с указанным id позиции.
+ Parameters
  + id: `7944ef04-f831-11e5-7a69-971500188b19` (required, string) - id Счёта поставщика
  + positionID: `34f6344f-015e-11e6-9464-e4de0000006c` (required, string) - id позиции Счёта поставщика
  
### Получить позицию Счёта 
Запрос на получение отдельной позиции Счёта с указанным id.
+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление отдельной позиции Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/get_position_by_id.json) -->
        
### Изменить позицию Счёта 
Запрос на обновление отдельной позиции Счёта. Для обновления позиции нет каких-либо
 обязательных для указания в теле запроса полей. Только те, что вы желаете обновить.
+ Request Пример (application/json)
Пример запроса на обновление отдельной позиции в Счёте поставщика.
  + Body
      <!-- include(body/invoice_in/put_position_request.json) -->

+ Response 200 (application/json)
Успешный запрос. Результат - JSON представление обновлённой позиции Счёта поставщика.
  + Body
        <!-- include(body/invoice_in/put_position_response.json) -->

### Удалить позицию 
Запрос на удаление отдельной позиции Счёта с указанным id.

+ Response 200 (application/json)
Успешное удаление позиции Счёта.