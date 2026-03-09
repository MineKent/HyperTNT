---
icon: sliders-simple
---

# Конфигурация

Главный файл `plugins/HyperTNT/config.yml` управляет глобальными настройками плагина.

## Структура файла

```yml
config-version: 2

settings:
  locale: ru_RU

tnts:
  sources:
    - "example.yml"
```

## Параметры

### `config-version`

Версия формата конфигурации. Не изменяй вручную — используется плагином для миграции.

### `settings`

#### `locale`

* `locale` (опционально) — локаль для системных сообщений. По умолчанию `ru_RU`.

### `tnts.sources`

* `sources` (обязательно) — список YAML-файлов с типами TNT.

Пути указываются относительно папки `plugins/HyperTNT/tnts/`.

Поддерживаются:
* YAML-файлы (например, `example.yml`) — могут содержать несколько типов TNT.
* Папки (например, `packs`) — из папки будут загружены все `*.yml` рекурсивно.

```yml
tnts:
  sources:
    - "example.yml"
    - "military.yml"
    - "special/chaos.yml"
    - "packs"
```

> [!NOTE]
> Файлы из `sources` читаются в порядке списка. Если два файла объявляют тип с одинаковым `id` — второй перезапишет первый.

## messages.yml

Файл `plugins/HyperTNT/messages.yml` содержит все тексты плагина. Поддерживает цвета через `&`-коды и плейсхолдеры `{...}`.

```yml
prefix: "&8[&cHyperTNT&8] &r"

errors:
  no-permission: "{prefix}&cНедостаточно прав."
  player-not-found: "{prefix}&cИгрок не найден."
  type-not-found: "{prefix}&cТип динамита не найден: &f{type}&c."
  invalid-number: "{prefix}&cНекорректное число."

commands:
  help:
    - "{prefix}&fКоманды:"
    - "&7/hypertnt give <игрок> <тип> [кол-во]"
    - "&7/hypertnt reload"
  reloaded: "{prefix}&aКонфиг перезагружен."
  given: "{prefix}&aВыдано &f{amount} &aшт. типа &f{type}&a игроку &f{player}&a."
```

> [!TIP]
> После изменения `messages.yml` выполни `/hypertnt reload` — файл перечитается без рестарта сервера.

## См. также

* [Быстрый старт](02-quick-start.md)
* [Предмет (item)](<Типы TNT/01-item.md>)
* [Команды](04-commands.md)
