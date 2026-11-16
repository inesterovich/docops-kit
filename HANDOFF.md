# HANDOFF — состояние работ

> Перезаписывается в конце каждого окна. Не история, а срез.
> История — `docs/sessions/`, идеи — `IDEAS.md`, план — `PLAN.md`.

## Рабочий каталог

`e:\Рабочие файлы\Илья\Программирование\docops-kit`
Репозиторий: https://github.com/inesterovich/docops-kit.git · ветка `main`

## Текущее окно

1 · Каркас `base/` + `core/` — завершено. Следующее: окно 2 «SPEC, правила, пресеты, ADR».

## Цель ближайшего шага

`core/SPEC.template.md`; `rules/universal-rules.md` (`KIT-1…KIT-15` с родословной);
`presets/README.md` и три группы пресетов; `docs/decisions/ADR-0001-docops-kit.md`, `ADR-0002-presets-per-group.md`.

## Сделано

- Окно 0: `PLAN.md`, `HANDOFF.md`, `IDEAS.md`, `.gitignore` — коммит `9291d88`.
- Окно 1 — коммит `027e2fb` (`feat: каркас base/ и core/, профили minimal/standard/full`):
  `base/` — `.gitignore`, `.gitattributes`, `.editorconfig`, `LICENSE`;
  `core/` — `AGENTS.template.md` (13 разделов), `README.template.md`, `CHANGELOG.template.md`, `NOTES.template.md`;
  `profiles/` — `minimal.md`, `standard.md`, `full.md`; `docs/sessions/S-01.md`.
- Дополнение после закрытия окна: `docs/prompts/S-02.md`, правило 5 в `PLAN.md`, пункт в `AGENTS.template.md` §8, «Входной промпт» в `S-01`.

## Сломано / в работе

Ничего. Линтера `node checks/docs.test.js` ещё нет (окно 4) — проверки окна 1 сделаны скриптом на `node -e`.

## Проверки окна 1

| Команда | Ожидание | Статус |
|---|---|---|
| `node -e` обход 8 новых файлов на относительные ссылки | битых нет | ✅ 3 ссылки, все — на существующие профили |
| `node -e` заголовки `core/AGENTS.template.md` | 13 разделов, §8 и §13 на месте | ✅ 13; шаг 0 (`pwd`, `git rev-parse --show-toplevel`, `git remote -v`), KIT-15 |
| `node -e` баланс `{{` / `}}` | открытых = закрытых, имён 8 | ✅ 17 = 17 |
| `grep -n "node checks/docs.test.js" profiles/*` | одна команда, различие только флагом | ✅ `full` — `--report strict` |
| `test -d .github` | каталога нет | ✅ нет |
| `git status --short` | пусто между окнами | ✅ пусто после коммита |

## Промпт следующего окна

[docs/prompts/S-02.md](docs/prompts/S-02.md) — готов к вставке в новый чат, править не нужно.

## Вопросы к пользователю

Блокирующих нет. Открыто: `LICENSE` самого набора в корне (сейчас MIT только в `base/LICENSE` как шаблон) — решается в окне 6 вместе с README и CHANGELOG набора.

## Не делать в следующем окне

- Не тянуть CI/CD (`.github/`, workflows) — `IDEAS.md` I-04, отклонено.
- Не создавать полностековый пресет — I-01, отклонено.
- Не пинить версии в пресетах — проверка №21.
- Не ссылаться на ещё не существующие файлы (`rules/`, `presets/`, `checks/`): ссылки добавляются в окнах 2 и 4.
