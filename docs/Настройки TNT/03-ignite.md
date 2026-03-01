---
icon: bolt
---

# Поджиг (ignite)

Секция `ignite` управляет поведением TNT в момент поджига: время горения фитиля, физика движения, бросок и способы воспламенения.

## Синтаксис

```yml
<id>:
  ignite:
    fuse-seconds: 4.0
    auto-ignite-on-place: true
    velocity:
      gravity: true
      upward: 0.2
    throw:
      enabled: true
      velocity-xz: 0.9
      velocity-y: 0.2
    allow:
      flint-and-steel: true
      fire-charge: true
      redstone: true
      fire: true
      explosion: true
```

---

## Параметры фитиля

### `fuse-seconds`

* `fuse-seconds` (опционально) — время горения фитиля в секундах. По умолчанию `4.0`.

### `auto-ignite-on-place`

* `auto-ignite-on-place` (опционально) — автоматически поджигать TNT при установке блока. По умолчанию `true`.

> [!NOTE]
> Если `auto-ignite-on-place: false`, TNT ведёт себя как обычный блок до внешнего воздействия.

---

## Физика движения (`velocity`)

Настройки гравитации и начального импульса горящей TNT-сущности.

* `gravity` (опционально) — включить гравитацию у горящего TNT. По умолчанию `true`.
* `upward` (опционально) — начальный импульс вверх при поджиге (в блоках/тик). По умолчанию `0.0`.

```yml
velocity:
  gravity: false
  upward: 0.5
```

> [!TIP]
> Сочетай `gravity: false` с `throw` для броска по прямой траектории.

---

## Бросок (`throw`)

Настройка броска TNT правым кликом с предметом в руке.

* `enabled` (опционально) — разрешить бросок. По умолчанию `false`.
* `velocity-xz` (опционально) — горизонтальная скорость броска. По умолчанию `0.9`.
* `velocity-y` (опционально) — вертикальная составляющая броска. По умолчанию `0.2`.

```yml
throw:
  enabled: true
  velocity-xz: 1.2
  velocity-y: 0.4
```

---

## Способы поджига (`allow`)

Разрешённые способы поджига. Каждый ключ — `true` (разрешено) или `false` (запрещено).

| Ключ               | Описание                                              | По умолчанию |
|--------------------|-------------------------------------------------------|--------------|
| `flint-and-steel`  | Поджиг кремнём и сталью                               | `true`       |
| `fire-charge`      | Поджиг огненным шаром                                 | `true`       |
| `redstone`         | Поджиг редстоун-сигналом                              | `true`       |
| `fire`             | Поджиг огнём (блок огня рядом)                        | `true`       |
| `explosion`        | Цепная реакция (взрыв соседнего TNT поджигает этот)  | `true`       |

```yml
allow:
  flint-and-steel: true
  fire-charge: false
  redstone: true
  fire: false
  explosion: true
```

## См. также

* [Предмет (item)](01-item.md)
* [Взрыв (explosion)](05-explosion.md)
* [Голограмма и визуал](04-visual-hologram.md)
* [Примеры](<../Примеры/01-examples.md>)
