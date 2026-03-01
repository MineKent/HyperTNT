---
icon: wand-magic-sparkles
---

# Голограмма и визуал

Секция `visual` объединяет все визуальные эффекты горящей TNT-сущности: свечение и голограмму.

## Синтаксис

```yml
<id>:
  visual:
    glow:
      enabled: true
      color: RED
      animation:
        enabled: false
        colors: [RED, GOLD, YELLOW]
        period-ticks: 10
    hologram:
      enabled: true
      lines:
        - "&c&lHyperTNT"
        - "&7Взрыв через: &c{time}s"
      height: 1.2
      update-period-ticks: 5
```

---

## Свечение (`visual.glow`)

Свечение горящей TNT-сущности. К предмету в инвентаре отношения не имеет.

* `enabled` (опционально) — включить свечение. По умолчанию `false`.
* `color` (опционально) — цвет свечения. Используется когда `animation.enabled: false`. По умолчанию `RED`.

Допустимые значения `color`:

`BLACK`, `DARK_BLUE`, `DARK_GREEN`, `DARK_AQUA`, `DARK_RED`, `DARK_PURPLE`, `GOLD`, `GRAY`, `DARK_GRAY`, `BLUE`, `GREEN`, `AQUA`, `RED`, `LIGHT_PURPLE`, `YELLOW`, `WHITE`

### `glow.animation`

Анимация циклической смены цвета свечения. Работает только при `glow.enabled: true`.

* `enabled` (опционально) — включить анимацию. По умолчанию `false`.
* `colors` (опционально) — список цветов для анимации в порядке их смены.
* `period-ticks` (опционально) — интервал смены цвета в тиках. По умолчанию `10`.

```yml
glow:
  enabled: true
  color: RED
  animation:
    enabled: true
    colors: [DARK_RED, RED, GOLD, YELLOW, WHITE]
    period-ticks: 5
```

> [!NOTE]
> Свечение реализовано через scoreboard teams. Анимация активна только пока TNT горит — после взрыва эффект снимается автоматически.

---

## Голограмма (`visual.hologram`)

Плавающий текст над горящим TNT, обновляющийся в реальном времени.

* `enabled` (опционально) — показывать голограмму. По умолчанию `false`.
* `lines` (опционально) — список строк текста. Поддерживает `&`-коды цветов и плейсхолдер `{time}`.
* `height` (опционально) — высота голограммы над TNT в блоках. По умолчанию `1.2`.
* `update-period-ticks` (опционально) — интервал обновления текста в тиках. По умолчанию `5`.

Доступные плейсхолдеры в `lines`:

| Плейсхолдер | Описание                                      |
|-------------|-----------------------------------------------|
| `{time}`    | Оставшееся время до взрыва в секундах (float) |

```yml
visual:
  hologram:
    enabled: true
    lines:
      - "&c&lHyperTNT"
      - "&7Взрыв через: &c{time}s"
    height: 1.2
    update-period-ticks: 5
```

> [!TIP]
> Уменьши `update-period-ticks` до `1` для плавного отсчёта, но учитывай нагрузку при большом числе горящих TNT.

---

## См. также

* [Предмет (item)](01-item.md)
* [Поджиг (ignite)](02-ignite.md)
* [Примеры](<../Примеры/01-examples.md>)
