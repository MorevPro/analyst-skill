# Аналитик для OpenCode

Skill системного аналитика для корпоративного ноутбука. Он читает Jira, Confluence и PostgreSQL через **уже подключённые локальные MCP**, отдельно собирает полный список задач, сохраняет исходный контекст и формирует один `task.md` с постановкой и PlantUML.

## Установка

OpenCode ищет skills в `~/.config/opencode/skills/<name>/SKILL.md` и в `.opencode/skills/<name>/SKILL.md` проекта. Склонируйте этот репозиторий в глобальный каталог skills:

```sh
git clone https://github.com/MorevPro/analyst-skill.git ~/.config/opencode/skills/analyst
```

Для обновления:

```sh
git -C ~/.config/opencode/skills/analyst pull --ff-only
```

## Запуск

Запустите `opencode` и введите запрос:

```text
Используй skill analyst. Вызови Jira MCP, Confluence MCP и PostgreSQL MCP для задачи ABC-123. Получи список связанных задач отдельным вызовом Jira MCP, затем собери полный контекст по каждому источнику. Подготовь единый task.md с исходными данными, системным анализом и PlantUML.
```

Можно указать JQL/фильтр вместо одного ключа и свой путь результата. По умолчанию файл появится в `~/analyst-tasks/<КЛЮЧ>/task.md`, вне Git-репозитория. Skill не меняет Jira, Confluence или PostgreSQL.

## Ограничения

Точность и полнота зависят от прав MCP и заданной границы выборки. Если источник обрезает ответ, не даёт вложение или БД меняется во время чтения, skill должен записать этот пробел в `task.md`, а не скрывать его.
