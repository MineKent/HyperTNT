---
icon: memo-circle-check
---

# Примеры

Готовые рабочие конфигурации типов TNT. Каждый пример можно скопировать в свой файл источника и сразу использовать.

В одном файле можно определять несколько типов TNT. Каждый тип — ключ верхнего уровня файла.

---

## Стандартный TNT (default)

Базовый кастомный динамит с голограммой, свечением и броском.

```yml
default:
  enabled: true
  item:
    material: TNT
    name: "&c&lHyperTNT"
    lore:
      - "&7Особый динамит"
      - "&7Время до взрыва: &c{fuse}s"
  ignite:
    fuse-seconds: 4.0
    auto-ignite-on-place: true
    velocity:
      gravity: true
      upward: 0.2
    throw:
      enabled: true
      hand: mainhand
      velocity-xz: 0.9
      velocity-y: 0.2
    allow:
      flint-and-steel: true
      fire-charge: true
      redstone: true
      fire: true
      explosion: true
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
  explosion:
    radius: 6.0
    damage:
      enabled: true
      max-damage: 24.0
      min-damage: 0.0
      exposure: 1.0
    raycast:
      rays: 16
      strength-multiplier: 1.0
      resistance-multiplier: 1.0
    blocks:
      default:
        mode: BREAK
        drop-chance: 1.0
      per-material:
        OBSIDIAN:
          mode: IGNORE
        CHEST:
          mode: BREAK
          drop-chance: 1.0
    post:
      set-fire: false
      fire-chance: 0.2
      commands: []
```

---

## Ядерный заряд (nuclear)

Большой радиус, высокий урон, поджигает зону взрыва. Нельзя поджечь огнём или цепной реакцией.

```yml
nuclear:
  enabled: true
  item:
    material: TNT
    name: "&4&lЯдерный заряд"
    lore:
      - "&7Радиус: &c20 блоков"
      - "&7Урон: &c5–40"
      - "&7Время горения: &c{fuse}s"
  ignite:
    fuse-seconds: 6.0
    auto-ignite-on-place: true
    velocity:
      gravity: true
      upward: 0.0
    throw:
      enabled: false
    allow:
      flint-and-steel: true
      fire-charge: true
      redstone: true
      fire: false
      explosion: false
  visual:
    glow:
      enabled: true
      color: DARK_RED
      animation:
        enabled: true
        colors: [DARK_RED, RED, GOLD, YELLOW]
        period-ticks: 8
    hologram:
      enabled: true
      lines:
        - "&4&lЯДЕРНЫЙ ЗАРЯД"
        - "&cВзрыв через: &f{time}s"
      height: 1.5
      update-period-ticks: 2
  explosion:
    radius: 20.0
    damage:
      enabled: true
      max-damage: 40.0
      min-damage: 5.0
      exposure: 0.9
    raycast:
      rays: 24
      strength-multiplier: 1.2
      resistance-multiplier: 0.8
    blocks:
      default:
        mode: BREAK
        drop-chance: 0.0
      per-material:
        OBSIDIAN:
          mode: IGNORE
        BEDROCK:
          mode: IGNORE
        CHEST:
          mode: BREAK
          drop-chance: 1.0
    post:
      set-fire: true
      fire-chance: 0.4
      commands: []
```

---

## Бесшумная мина (silent)

Не разрушает блоки, наносит урон только существам. Не реагирует на редстоун.

```yml
silent:
  enabled: true
  item:
    material: TNT
    name: "&8&lБесшумная мина"
    lore:
      - "&7Не разрушает блоки"
      - "&7Только урон по существам"
  ignite:
    fuse-seconds: 2.0
    auto-ignite-on-place: true
    velocity:
      gravity: false
      upward: 0.0
    throw:
      enabled: true
      hand: mainhand
      velocity-xz: 0.6
      velocity-y: 0.1
    allow:
      flint-and-steel: true
      fire-charge: false
      redstone: false
      fire: false
      explosion: false
  visual:
    glow:
      enabled: true
      color: DARK_GRAY
      animation:
        enabled: false
    hologram:
      enabled: false
  explosion:
    radius: 5.0
    damage:
      enabled: true
      max-damage: 18.0
      min-damage: 2.0
      exposure: 1.0
    raycast:
      rays: 12
      strength-multiplier: 1.0
      resistance-multiplier: 1.0
    blocks:
      default:
        mode: IGNORE
    post:
      set-fire: false
      fire-chance: 0.0
      commands: []
```

---

## TNT с крафтом (craftable)

Тип с включённым крафтом: 8 пороха вокруг обычного TNT.

```yml
craftable:
  enabled: true
  item:
    material: TNT
    name: "&6&lКрафтовый TNT"
    lore:
      - "&7Скрафти его сам!"
  ignite:
    fuse-seconds: 3.5
    auto-ignite-on-place: true
    velocity:
      gravity: true
      upward: 0.0
    throw:
      enabled: false
    allow:
      flint-and-steel: true
      fire-charge: true
      redstone: true
      fire: true
      explosion: true
  craft:
    enabled: true
    shape:
      - "GGG"
      - "GTG"
      - "GGG"
    ingredients:
      G: GUNPOWDER
      T: TNT
  visual:
    glow:
      enabled: false
    hologram:
      enabled: false
  explosion:
    radius: 7.0
    damage:
      enabled: true
      max-damage: 20.0
      min-damage: 0.0
      exposure: 1.0
    blocks:
      default:
        mode: BREAK
        drop-chance: 0.8
    post:
      set-fire: false
      commands: []
```

## См. также

* [Предмет (item)](<../Типы TNT/01-item.md>)
* [Поджиг (ignite)](<../Типы TNT/02-ignite.md>)
* [Взрыв (explosion)](<../Типы TNT/05-explosion.md>)
* [Голограмма и визуал](<../Типы TNT/04-visual-hologram.md>)
* [Команды](../Команды/01-commands.md)
