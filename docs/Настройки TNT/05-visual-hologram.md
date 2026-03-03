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

    sounds:
      ignite:
        enabled: true
        sound: ENTITY_TNT_PRIMED
        volume: 1.0
        pitch: 1.0
      explosion:
        enabled: true
        sound: ENTITY_GENERIC_EXPLODE
        volume: 4.0
        pitch: 1.0

    particles:
      enabled: false
      type: FLAME
      count: 30
      offset:
        x: 0.5
        y: 0.5
        z: 0.5
      extra: 0.02

    hologram:
      enabled: true
      lines:
        - "&c&lHyperTNT"
        - "&7Взрыв через: &c{time}s"
      height: 1.2
      update-period-ticks: 5
```

---

## Звуки (`visual.sounds`)

Секция `sounds` содержит две подсекции: `ignite` (звук поджога) и `explosion` (звук взрыва).

```yml
visual:
  sounds:
    ignite:
      enabled: true
      sound: ENTITY_TNT_PRIMED
      volume: 1.0
      pitch: 1.0

    explosion:
      enabled: true
      sound: ENTITY_GENERIC_EXPLODE
      volume: 4.0
      pitch: 1.0
```

### `visual.sounds.ignite` — звук поджога

Проигрывается в момент успешной активации TNT (при любом сценарии поджига).

* `enabled` (опционально) — включить звук поджога. По умолчанию: `true`.
  * Если `false` или секция отсутствует — звук поджога не переопределяется.
* `sound` (опционально) — имя звука из `org.bukkit.Sound`. По умолчанию: `ENTITY_TNT_PRIMED`.
* `volume` (опционально) — громкость. По умолчанию: `1.0`.
* `pitch` (опционально) — тон. По умолчанию: `1.0`.

### `visual.sounds.explosion` — звук взрыва

Проигрывается при **кастомном** взрыве HyperTNT.

* `enabled` (опционально) — включить звук взрыва. По умолчанию: `true`.
  * Если `false` — звук взрыва не проигрывается (тишина).
* `sound` (опционально) — имя звука из `org.bukkit.Sound`. По умолчанию: `ENTITY_GENERIC_EXPLODE`.
* `volume` (опционально) — громкость. По умолчанию: `4.0`.
* `pitch` (опционально) — тон. По умолчанию: `1.0`.

> [!NOTE]
> Если указано неверное имя звука — используется безопасный дефолт (`ENTITY_TNT_PRIMED` / `ENTITY_GENERIC_EXPLODE`) и в консоль выводится предупреждение.

> [!TIP]
> **Обратная совместимость:** старый формат (`enabled/sound/volume/pitch` на уровне `sounds`) без подсекций всё ещё читается и воспринимается как настройка звука **взрыва**.

---

## Частицы при взрыве (`visual.particles`)

Дополнительные частицы, которые будут спавниться при взрыве TNT этого типа.

* `enabled` (опционально) — включить/выключить частицы.
  * По умолчанию: `false`.
* `type` (опционально) — имя частицы из `org.bukkit.Particle`.
  * По умолчанию: `FLAME`.
* `count` (опционально) — количество частиц.
  * По умолчанию: `30`.
* `offset.x/y/z` (опционально) — разброс по осям.
  * По умолчанию: `0.5`.
* `extra` (опционально) — параметр speed ("extra") у `World#spawnParticle`.
  * По умолчанию: `0.02`.

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

* [Предмет (item)](02-item.md)
* [Поджиг (ignite)](03-ignite.md)
* [Примеры](<../Примеры/01-examples.md>)
