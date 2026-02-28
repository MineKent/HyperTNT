---
icon: wand-magic-sparkles
---

# Голограмма и визуал

Секции `hologram` и `item.glow-animation` управляют визуальным отображением горящего TNT: текстом над сущностью и анимацией свечения.

## Голограмма (`hologram`)

Плавающий текст над горящим TNT, обновляющийся в реальном времени.

### Синтаксис

```yml
<id>:
  hologram:
    enabled: true
    lines:
      - "&c&lHyperTNT"
      - "&7Взрыв через: &c{time}s"
    height: 1.2
    update-period-ticks: 5
```

### Параметры

* `enabled` (опционально) — показывать голограмму. По умолчанию `false`.
* `lines` (опционально) — список строк текста. Поддерживает `&`-коды цветов и плейсхолдер `{time}`.
* `height` (опционально) — высота голограммы над TNT в блоках. По умолчанию `1.2`.
* `update-period-ticks` (опционально) — интервал обновления текста в тиках. По умолчанию `5`.

Доступные плейсхолдеры в `lines`:

| Плейсхолдер | Описание                                      |
|-------------|-----------------------------------------------|
| `{time}`    | Оставшееся время до взрыва в секундах (float) |

> [!TIP]
> Уменьши `update-period-ticks` до `1` для плавного отсчёта, но учитывай нагрузку при большом числе горящих TNT.

---

## Анимация свечения (`glow-animation`)

Циклическая смена цвета свечения у горящего TNT.

### Синтаксис

```yml
<id>:
  item:
    glowing: true
    glow-color: RED
    glow-animation:
      enabled: true
      colors: [RED, GOLD, YELLOW]
      period-ticks: 10
```

### Параметры

* `glowing` (обязательно для анимации) — свечение должно быть включено (`true`).
* `glow-color` — базовый цвет свечения (используется если `glow-animation.enabled: false`).
* `glow-animation.enabled` (опционально) — включить анимацию смены цвета. По умолчанию `false`.
* `glow-animation.colors` (опционально) — список цветов, по которым проходит анимация. Порядок соблюдается.
* `glow-animation.period-ticks` (опционально) — интервал смены одного цвета в тиках. По умолчанию `10`.

Допустимые цвета:

`BLACK`, `DARK_BLUE`, `DARK_GREEN`, `DARK_AQUA`, `DARK_RED`, `DARK_PURPLE`, `GOLD`, `GRAY`, `DARK_GRAY`, `BLUE`, `GREEN`, `AQUA`, `RED`, `LIGHT_PURPLE`, `YELLOW`, `WHITE`

```yml
glow-animation:
  enabled: true
  colors: [DARK_RED, RED, GOLD, YELLOW, WHITE]
  period-ticks: 5
```

> [!NOTE]
> Анимация свечения активируется только пока TNT горит. После взрыва эффект снимается автоматически.

## См. также

* [Предмет (item)](01-item.md)
* [Поджиг (ignite)](02-ignite.md)
* [Примеры](<../Примеры/01-examples.md>)
