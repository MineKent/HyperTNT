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
      particle: FLAME
      count: 30
      offset-x: 0.5
      offset-y: 0.5
      offset-z: 0.5
      extra: 0.02

    hologram:
      enabled: true
      type: armorstand # armorstand/displaytext
      lines:
        - "&c&lHyperTNT"
        - "&7Взрыв через: &c{time}s"
      height: 1.2
      line-spacing: 0.25
      update-period-ticks: 5
      displaytext:
        shadowed: true
        see-through: false
        default-background: false
        background-color: "#00000000"
        line-width: 200
        text-opacity: 255
        billboard: FIXED
        alignment: CENTER
        scale: 1.0
        glowing: false
        glow-color: "#FFFFFF"
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
* `particle` (опционально) — имя частицы из `org.bukkit.Particle`.
  * По умолчанию: `FLAME`.
* `count` (опционально) — количество частиц.
  * По умолчанию: `30`.
* `offset-x/y/z` (опционально) — разброс по осям.
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
* `type` (опционально) — тип голограммы: `armorstand` или `displaytext`. По умолчанию `armorstand`.
* `lines` (опционально) — список строк текста. Поддерживает `&`-коды цветов и плейсхолдер `{time}`.
* `height` (опционально) — высота голограммы над TNT в блоках. По умолчанию `1.2`.
* `line-spacing` (опционально) — расстояние между строками. По умолчанию `0.25`.
* `update-period-ticks` (опционально) — интервал обновления текста в тиках. По умолчанию `5`.

Доступные плейсхолдеры в `lines`:

| Плейсхолдер | Описание                                      |
|-------------|-----------------------------------------------|
| `{time}`    | Оставшееся время до взрыва в секундах (float) |

```yml
visual:
  hologram:
    enabled: true
    type: displaytext
    lines:
      - "&c&lHyperTNT"
      - "&7Взрыв через: &c{time}s"
    height: 1.2
    line-spacing: 0.25
    update-period-ticks: 5
```

> [!TIP]
> Уменьши `update-period-ticks` до `1` для плавного отсчёта, но учитывай нагрузку при большом числе горящих TNT.

### `hologram.displaytext` (только для `type: displaytext`)

Дополнительные настройки для режима `displaytext`. Этот режим использует сущности `TextDisplay` и доступен только на версиях, где они существуют (примерно 1.19+). Если сервер не поддерживает `TextDisplay`, плагин автоматически откатится к `armorstand`.

* `shadowed` — тень текста. По умолчанию `true`.
* `see-through` — текст виден сквозь блоки. По умолчанию `false`.
* `default-background` — дефолтный фон текста. По умолчанию `false`.
* `background-color` — цвет фона в hex (`#RRGGBB` или `#AARRGGBB`). По умолчанию не задан.
* `line-width` — ширина строки (перенос). По умолчанию `200`.
* `text-opacity` — прозрачность текста `0..255`. По умолчанию `255`.
* `billboard` — режим поворота (например `FIXED`, `CENTER`). По умолчанию `FIXED`.
* `alignment` — выравнивание текста (например `CENTER`, `LEFT`, `RIGHT`). По умолчанию `CENTER`.
* `scale` — масштаб. По умолчанию `1.0`.
* `glowing` — включить свечение сущности. По умолчанию `false`.
* `glow-color` — цвет свечения в hex (`#RRGGBB` или `#AARRGGBB`). По умолчанию не задан.

```yml
visual:
  hologram:
    enabled: true
    type: displaytext
    lines:
      - "&f{time}"
    height: 1.2
    line-spacing: 0.25
    update-period-ticks: 2
    displaytext:
      shadowed: true
      see-through: false
      default-background: false
      background-color: "#00000000"
      line-width: 200
      text-opacity: 255
      billboard: FIXED
      alignment: CENTER
      scale: 1.0
      glowing: false
      glow-color: "#FFFFFF"
```

---

## См. также

* [Предмет (item)](02-item.md)
* [Поджиг (ignite)](03-ignite.md)
* [Условия (conditions)](05-conditions.md)
* [Взрыв (explosion)](07-explosion.md)
* [Примеры](<../Примеры/01-examples.md>)
