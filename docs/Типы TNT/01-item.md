---
icon: bolt
---

# Предмет (item)

Секция `item` описывает внешний вид предмета TNT в инвентаре: материал, название, лор и свечение.

## Синтаксис

```yml
tnts:
  <id>:
    item:
      material: TNT
      name: "&c&lHyperTNT"
      lore:
        - "&7Особый динамит"
        - "&7Время до взрыва: &c{fuse}s"
      glowing: true
      glow-color: RED
      glow-animation:
        enabled: false
        colors: [RED, GOLD, YELLOW]
        period-ticks: 10
```

### `material`

* `material` (обязательно) — Bukkit-имя материала предмета. По умолчанию `TNT`.

Примеры допустимых значений: `TNT`, `GUNPOWDER`, `FIRE_CHARGE`, `NETHER_STAR`.

### `name`

* `name` (опционально) — отображаемое название предмета. Поддерживает `&`-коды цветов и PlaceholderAPI.

### `lore`

* `lore` (опционально) — список строк описания предмета. Поддерживает `&`-коды и плейсхолдер `{fuse}`.

Доступные плейсхолдеры в `lore`:

| Плейсхолдер | Описание                        |
|-------------|---------------------------------|
| `{fuse}`    | Время горения фитиля в секундах |

### `glowing`

* `glowing` (опционально) — включает эффект свечения предмета. По умолчанию `false`.

### `glow-color`

* `glow-color` (опционально) — цвет свечения. По умолчанию `WHITE`.

Допустимые значения:

`BLACK`, `DARK_BLUE`, `DARK_GREEN`, `DARK_AQUA`, `DARK_RED`, `DARK_PURPLE`, `GOLD`, `GRAY`, `DARK_GRAY`, `BLUE`, `GREEN`, `AQUA`, `RED`, `LIGHT_PURPLE`, `YELLOW`, `WHITE`

### `glow-animation`

Анимация смены цвета свечения у горящего TNT.

* `enabled` (опционально) — включить анимацию. По умолчанию `false`.
* `colors` (опционально) — список цветов для анимации. Перечисляются через запятую в квадратных скобках.
* `period-ticks` (опционально) — интервал смены цвета в тиках. По умолчанию `10`.

```yml
glow-animation:
  enabled: true
  colors: [RED, GOLD, YELLOW]
  period-ticks: 10
```

> [!TIP]
> Свечение работает через механику команд скора (scoreboard teams). Цвет задаётся через `ChatColor`, соответствующий значению `glow-color`.

## См. также

* [Поджиг (ignite)](02-ignite.md)
* [Голограмма и визуал](04-visual-hologram.md)
* [Быстрый старт](../02-quick-start.md)
