# stolenX - harness

Фреймворк для агентской разработки

## Структура проекта

```
.
├── .github/                 # шаблоны PR и issue, CONTRIBUTING.md
├── .husky/                  # git-хуки: commit-msg, pre-commit
├── documentation/           # правила и документация проекта
├── CLAUDE.md                # инструкции для агента
├── commitlint.config.mjs    # правила формата коммитов
├── package.json
└── package-lock.json
```

## Работа с git

Ветка на задачу, небольшие коммиты в формате [Conventional Commits](https://www.conventionalcommits.org/), PR по шаблону.

| Что | Формат | Пример |
|---|---|---|
| Ветка | `<тип>/<описание>` | `feat/user-profile`, `fix/482-token-loop` |
| Коммит | `<тип>(<область>): <описание>` | `fix(auth): prevent token refresh loop` |
| Типы | `feat` `fix` `docs` `refactor` `test` `chore` `perf` `ci` | |

Прямые коммиты в `main` запрещены.

### Автоматические проверки

| Хук | Что проверяет |
|---|---|
| `pre-commit` | имя ветки соответствует формату, коммит не в `main` |
| `commit-msg` | сообщение коммита проходит commitlint |

Если хук отклонил коммит, исправьте сообщение или имя ветки. Не обходите хуки через `--no-verify`.

Подробные правила и шаблоны: [`.github/CONTRIBUTING.md`](.github/CONTRIBUTING.md).

## Работа с агентом

Агент читает [`CLAUDE.md`](CLAUDE.md) и следует его правилам. Основные принципы:

- завершить ответ не значит сделать коммит;
- ветка создаётся на задачу, а не на каждый ответ;
- push, PR и issue только по явной просьбе;
- при неуверенности агент спрашивает, а не угадывает.