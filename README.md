# OGSM Spawner — Trainer-Style Menu Mod

**Версия:** 1.5 
**Игра:** S.T.A.L.K.E.R.: Shadow of Chernobyl 1.0006  
**Мод:** OGSM 2.4.3 Gold Edition  
**Файлов:** 3 (2 new + 1 modified)

---

## Changelog

### v1.5 Fixes
- Исправлены вылеты из-за секций артов
- Убраны торговцы из спавнера
- Правки интерфейса: сетка предметов с 3 колонок на 2 колонки × 5 рядов, теперь кнопки шире (235-240px вместо 150-160px)
- Теперь пишется какие арты выводят радиацию

### v1.4 — Expansion 
- AIM: фиксированная дистанция 15 м + фоллбэк `{5, 20, 25}`
- Burst: spread 10-18 м, retry до 5 попыток с рандомными углами
- Mutants: (dogs, pseudodogs, flesh, snork, boar, zombies, bloodsuckers, burers, controllers, chimeras, poltergeists, gigants, tushkanos)
- Equipment: 17 → 31 (drug_fluor + 13 outfits)

### v1.3 — Fixes
- Удалены `sobj.position = pos` / `sobj.level_vertex_id = lvid` / `sobj.game_vertex_id = center_gvid` — READ-ONLY в X-Ray 1.0006, запись = Lua exception → burst прерывался на 1 итерации
- Добавлен `pcall(wait)` между `alife():create` для anti-coalescing
- SetStatus warning на silent fallbacks

### v1.2 — Burst & aim reliability
- Multi-step + multi-angle retry: 5 попыток, радиусы `[10,18]→[4,8]`
- Убран redundant type-check guard

### v1.1 — Cam_dir & multi-distance cast
- 6-вариантный pcall chain для `cam_dir` (property / method / device / actor)
- Multi-distance AIM: 15 м → `{5, 10, 20, 8, 22, 5, 25}`
- Burst radius: 2-5 м → 10-18 м

### v1.0 — First
- 10 категорий (8 inventory + 2 world)
- Target/Aim toggle, Cluster 1x/3x/5x
- F1 хоткей + кнопка "Спавнер" в ESC-меню



---

## Установка

1. Скопируй `gamedata/` из архива в `<STALKER>/gamedata/`:
   ```
   gamedata/scripts/ui_spawner.script
   gamedata/scripts/ui_main_menu.script
   gamedata/config/ui/ui_spawner_wnd.xml
   ```
2. Игра → ESC → F1 (или кнопка "Спавнер")
3. Категория слева → предмет справа 

---

## Файлы

| Файл | Тип | Назначение |
|------|-----|------------|
| `ui_spawner.script` | NEW | Скрипт спавнера (10 категорий, 41+ mutants, 31+ items, 39+ stalkers) |
| `ui_main_menu.script` | MODIFIED | F1 хоткей + кнопка "Спавнер" |
| `ui_spawner_wnd.xml` | NEW | UI окно 700×580, сетка 3×4 |

---

## Категории

| № | Категория | Kind | Содержимое |
|---|-----------|------|------------|
| 1 | Pistols | inv | PM, PB, Fort, HPSA, Beretta, Walther, SIG-220, Colt, USP, Desert Eagle |
| 2 | Assault / SMG | inv | AK-74U, AK-74, Abakan, MP-5, L85, LR-300, SIG-550, Groza, VSS, G36, FN2000 |
| 3 | Snipers | inv | SVD, SVU, Gauss |
| 4 | Shotguns | inv | BM-16, TOZ-34, Winchester 1300, SPAS-12 |
| 5 | Launchers | inv | RG-6, RPG-7, F-1, RGD-5 |
| 6 | Ammo | inv | 9x18/9x19/.45/5.45/5.56/7.62/9x39 (×60), 12ga, VOG, M209, OG-7B, Gauss |
| 7 | Artefacts | inv | Meduza, Crystal, Night Star, Vyvert, Gravi, Goldfish и др. |
| 8 | Equipment | inv | Meds, еда, детекторы, 13 outfits |
| 9 | Mutants | world | 41 секция из m_*.ltx |
| 10 | Stalkers | world | 39 секций из spawn_sections.ltx |

---

## Toggles (Mutants / Stalkers)

- **Target: Actor** — спавн ~8м от ГГ
- **Target: Aim** — спавн по лучу прицела (15 м, фоллбэк 5→20→25 м)
- **Cluster: 1x/3x/5x** — кол-во экземпляров, разнесённых по кругу (retry 5 попыток)

---

## Совместимо с OGSM 2.4

---

## Ограничения

- Торговцы спавнятся на логическом месте (по $spawn), не у актёра
- AIM без bullet-trace — аппроксимация через vertex_in_direction
- Burst 5x может вызвать frame stalls на старых CPU


---

## Credits

- Команда OGSM —  мод
- GSC Game World — STALKER
