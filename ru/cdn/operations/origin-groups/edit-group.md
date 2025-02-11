# Изменение группы источников

## Редактирование группы {#editing-groups}

Чтобы изменить [группу источников](../../concepts/origins.md):

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором хотите создать группу ресурсов.
  1. Выберите сервис **Cloud CDN**.
  1. На панели слева выберите ![image](../../../_assets/cdn/origin-groups.svg) **Группы источников**.
  1. Выберите группу, которую хотите отредактировать.
  1. В правом верхнем углу нажмите кнопку ![image](../../../_assets/pencil.svg) **Редактировать**.
  1. Внесите необходимые изменения.
  1. Нажмите кнопку **Сохранить**.

- CLI

  {% include [include](../../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

  1. Посмотрите описание команды CLI для редактирования группы источников:

     ```
     yc cdn origin-group update --help
     ```

  1. Получите список всех групп источников в каталоге по умолчанию:

     ```
     yc cdn origin-group list --format yaml
     ```

     Результат:

     ```
     - id: "90209"
       folder_id: b1g86q4m5vej8lkljme5
       name: test-group-1
       use_next: true
       origins:
       - id: "561547"
         origin_group_id: "90209"
         source: www.example2.com
         enabled: true
         backup: true
       - id: "561546"
         origin_group_id: "90209"
         source: www.example1.com
         enabled: true
     - id: "90208"
       folder_id: b1g86q4m5vej8lkljme5
       name: test-group
       use_next: true
       origins:
       - id: "561545"
         origin_group_id: "90208"
         source: www.a2.com
         enabled: true
         backup: true
       - id: "561544"
         origin_group_id: "90208"
         source: www.a1.com
         enabled: true
     ```
  
  1. Измените параметры группы источников, указав ее идентификатор:

     ```
     yc cdn origin-group update --id <идентификатор группы источников> \
       --name <новое имя группы> \
       --origin source=<IP-адрес или доменное имя нового источника>,enabled=true \
       --origin source=<IP-адрес или доменное имя нового источника>,enabled=true,backup=true
     ```

     Где `origin` — спецификация источника:
     * `source` — IP-адрес или доменное имя нового источника.
     * `enabled` — флаг, указывающий, включен ли источник.
     * `backup` — флаг, указывающий, является ли источник резервным.

     Результат:

     ```
     id: "90209"
     folder_id: b1g86q4m5vej8lkljme5
     name: test-group-22
     use_next: true
     origins:
     - id: "559307"
       origin_group_id: "90209"
       source: www.site2.com
       enabled: true
       backup: true
     - id: "559306"
       origin_group_id: "90209"
       source: www.site1.com
       enabled: true
     ```

     Подробнее о команде `yc cdn origin-group update` см. в [справочнике CLI](../../../cli/cli-ref/managed-services/cdn/origin-group/update.md).

{% endlist %}

## Удаление одного источника из группы {#group-source-deletion}

Чтобы удалить источник из группы источников:

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором хотите создать группу ресурсов.
  1. Выберите сервис **Cloud CDN**.
  1. На панели слева выберите ![image](../../../_assets/cdn/origin-groups.svg) **Группы источников** и нажмите на имя группы, из которой хотите удалить источник.
  1. Выберите нужный источник и нажмите кнопку **Удалить** на панели внизу.

      {% note info %}

      Удалить можно только резервный источник.

      {% endnote %}

  1. Подтвердите удаление.

{% endlist %}

## Удаление нескольких источников из группы {#summ-group-source-deletion}

Чтобы удалить несколько источников из группы:

{% list tabs %}

- Консоль управления

  1. В [консоли управления]({{ link-console-main }}) выберите каталог, в котором хотите создать группу ресурсов.
  1. Выберите сервис **Cloud CDN**.
  1. На панели слева выберите ![image](../../../_assets/cdn/origin-groups.svg) **Группы источников** и нажмите на имя группы, из которой хотите удалить источники.
  1. Выберите нужные источники и нажмите кнопку **Удалить** на панели внизу.

      {% note info %}

      Удалить можно только резервные источники.

      {% endnote %}

  1. Подтвердите удаление.

{% endlist %}
