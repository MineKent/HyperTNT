---
icon: power-off
---

# Быстрый старт

Минимальный набор шагов, чтобы запустить HyperTNT и получить первый кастомный динамит в игре.

## Установка

1. Скопируй `HyperTNT.jar` в папку `plugins/` сервера.
2. Запусти (или перезапусти) сервер — плагин создаст `plugins/HyperTNT/config.yml` и папку `tnts/`.
3. В `config.yml` уже прописан источник `example.yml` — он содержит тип `default`.

## Получение предмета

```bash
/hypertnt give <игрок> default [количество]
```

Пример:

```bash
/hypertnt give Steve default 5
```

> [!TIP]
> Команда требует право `hypertnt.admin` (по умолчанию — у операторов).

## Создание своего типа TNT

1. Создай файл `plugins/HyperTNT/tnts/my_tnts.yml`.
2. Добавь его в `config.yml` в раздел `tnts.sources`.
3. Опиши типы по формату:

```yml
tnts:
  nuclear:
    enabled: true
    item:
      material: TNT
      name: "&4&lЯдерный заряд"
      lore:
        - "&7Радиус взрыва: &c20 блоков"
      glowing: true
      glow-color: RED
    ignite:
      fuse-seconds: 5.0
      auto-ignite-on-place: true
    explosion:
      radius: 20.0
      damage:
        enabled: true
        max-damage: 40.0
        min-damage: 5.0
```

4. Выполни `/hypertnt reload` — плагин перечитает все файлы.
5. Выдай предмет: `/hypertnt give Steve nuclear`.

## Проверка доступных типов

```bash
/hypertnt types
```

Плагин ответит списком всех загруженных идентификаторов типов.

## См. также

* [Конфигурация](03-config.md)
* [Предмет (item)](<Типы TNT/01-item.md>)
* [Поджиг (ignite)](<Типы TNT/02-ignite.md>)
* [Взрыв (explosion)](<Типы TNT/03-explosion.md>)
