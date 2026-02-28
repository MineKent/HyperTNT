---
icon: bolt
---

# Поджиг (ignite)

Секция `ignite` управляет поведением TNT в момент поджига: время горения фитиля, гравитация, бросок и разрешённые способы воспламенения.

## Синтаксис

```yml
tnts:
  <id>:
    ignite:
      fuse-seconds: 4.0
      auto-ignite-on-place: true
      disable-gravity: false
      upward-velocity: 0.2
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

### `fuse-seconds`

* `fuse-seconds` (опционально) — время горения фитиля в секундах. По умолчанию `4.0`.

### `auto-ignite-on-place`

* `auto-ignite-on-place` (опционально) — автоматически поджигать TNT при установке блока. По умолчанию `true`.

> [!NOTE]
> Если `auto-ignite-on-place: false`, TNT ведёт себя как обычный блок до внешнего воздействия.

### `disable-gravity`

* `disable-gravity` (опционально) — отключить гравитацию у горящего TNT. По умолчанию `false`.

### `upward-velocity`

* `upward-velocity` (опционально) — начальный импульс вверх при поджиге (в блоках/тик). По умолчанию `0.2`.

Работает только при `auto-ignite-on-place: true` или поджиге через поддерживаемые методы.

### `throw`

Настройка броска TNT правым кликом с зажатым предметом в руке.

* `enabled` (опционально) — разрешить бросок. По умолчанию `false`.
* `velocity-xz` (опционально) — горизонтальная скорость броска. По умолчанию `0.9`.
* `velocity-y` (опционально) — вертикальная составляющая броска. По умолчанию `0.2`.

```yml
throw:
  enabled: true
  velocity-xz: 1.2
  velocity-y: 0.4
```

> [!TIP]
> Сочетай `throw` с `disable-gravity: true` для броска, при котором TNT летит по прямой.

### `allow`

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
* [Взрыв (explosion)](03-explosion.md)
* [Примеры](<../Примеры/01-examples.md>)
