# Lovable Workspace Skills Repository  

## Purpose  
A Russian‑first guide for creating, organizing, and maintaining **Lovable Workspace** skills. It explains the repository layout, how to transfer skill metadata into Lovable, provides a quick‑start for the six core skills, outlines workflow chains, and defines maintenance and versioning practices.

---  

## Repository Map  

| Directory / File | Description |
|------------------|-------------|
| `core/` | Six core skill definitions (JSON/YAML) |
| `chains/` | Pre‑built workflow chains that combine core skills |
| `docs/` | Additional documentation, examples, and diagrams |
| `scripts/` | Helper scripts (e.g., validation, linting) |
| `README.md` | This guide |
| `CHANGELOG.md` | Version history |
| `LICENSE` | Repository license |

---  

## Manual Transfer of Skill Metadata  

Each skill consists of three required fields: **Name**, **Description**, and **Instructions**. To import them into Lovable manually:

1. **Open the skill file** in `core/` (e.g., `core/translation_skill.json`).  
2. **Locate the metadata section** (top‑level keys).  
3. **Copy the values**:  
   - `Name` → the skill’s display name.  
   - `Description` → a short Russian‑language summary (≤ 120 characters).  
   - `Instructions` → detailed step‑by‑step guidance, written in Russian, using Markdown when needed.  
4. **Paste into Lovable UI**:  
   - Navigate to **Workspace → Skills → Add New**.  
   - Fill the three fields with the copied text.  
   - Click **Save**.  
5. **Validate**: Run the repository’s linter (`npm run lint` or `python -m scripts.lint`) to ensure JSON/YAML syntax is correct before uploading.  

> **Tip:** Keep the original files as the source of truth; any change must be reflected both in the repository and in Lovable.

---  

## Six Core Skills – Quick Start  

| Skill | Name (RU) | Description (RU) | Key Instructions |
|-------|-----------|-------------------|------------------|
| 1 | **Переводчик** | Быстрый перевод текста между языками. | 1. Введите исходный текст.<br>2. Выберите язык‑источник и язык‑цель.<br>3. Нажмите **Перевести**. |
| 2 | **Резюмирующий** | Сокращает длинные документы до ключевых пунктов. | 1. Вставьте документ.<br>2. Укажите желаемую длину резюме.<br>3. Нажмите **Создать резюме**. |
| 3 | **Анализатор Тональности** | Оценивает эмоциональную окраску текста. | 1. Введите текст.<br>2. Нажмите **Анализировать**.<br>3. Просмотрите шкалу от «негативно» до «позитивно». |
| 4 | **Генератор Идей** | Предлагает креативные идеи по заданной теме. | 1. Укажите тему/контекст.<br>2. Выберите количество вариантов.<br>3. Нажмите **Генерировать**. |
| 5 | **Планировщик Задач** | Создаёт список задач с приоритетами и сроками. | 1. Введите цель проекта.<br>2. Добавьте задачи и сроки.<br>3. Сохраните план. |
| 6 | **Контроль Версий** | Автоматически фиксирует изменения навыков. | 1. После изменения файла запустите `git commit -m "Update <skill>"`.<br>2. Тегируйте релиз (`git tag vX.Y.Z`). |

**Getting started:**  
```bash
# Clone the repo
git clone https://github.com/your-org/lovable-workspace-skills.git
cd lovable-workspace-skills

# Install optional linting tools
pip install -r requirements.txt
```
*(The above commands are illustrative; actual setup may vary.)*

---  

## Workflow Chains  

Workflow chains combine multiple core skills to solve complex tasks. Example chain: **Переводчик → Резюмирующий → Анализатор Тональности**.

1. **Create a chain file** in `chains/` (e.g., `translation_summary_sentiment.json`).  
2. Define the ordered list of skill IDs and data mapping between them.  
3. Upload the chain via Lovable UI → **Chains → Add New**.  
4. Test the chain with a sample input; adjust mappings if needed.  

Common ready‑made chains (found in `chains/`):

| Chain Name | Steps | Use Case |
|------------|-------|----------|
| `doc_localization` | Переводчик → Резюмирующий | Быстрая локализация и сокращение технической документации. |
| `feedback_analysis` | Анализатор Тональности → Генератор Идей | Оценка отзывов и генерация улучшений продукта. |
| `project_bootstrap` | Планировщик Задач → Генератор Идей | Планирование нового проекта с креативными предложениями. |

---  

## Maintenance & Versioning  

| Activity | Frequency | Procedure |
|----------|-----------|-----------|
| **Code linting** | On each PR | Run `scripts/lint.py`; fix any violations before merge. |
| **Skill validation** | Nightly | CI job executes `scripts/validate_skills.py` against all files in `core/`. |
| **Documentation update** | When a skill or chain changes | Edit `README.md` or relevant docs, then commit with `docs:` prefix. |
| **Release** | After a set of stable changes | 1. Merge to `main`.<br>2. Tag with semantic version (`vMAJOR.MINOR.PATCH`).<br>3. Update `CHANGELOG.md`. |
| **Backup** | Weekly | Push repository to a secondary remote (`git remote add backup …`). |

### Versioning Scheme  

- **MAJOR** – Breaking changes to skill schema or API.  
- **MINOR** – New skills, chains, or backward‑compatible enhancements.  
- **PATCH** – Bug fixes, linting, documentation tweaks.  

All releases are announced in the repository’s **Releases** page and include a short changelog.

---  

## Contributing  

1. Fork the repository.  
2. Create a feature branch (`git checkout -b feature/<name>`).  
3. Add or modify skill/chain files.  
4. Run lint & validation scripts.  
5. Open a Pull Request with a clear description (use the `feat:` or `fix:` prefix).  

---  

## License  

This repository is licensed under the **MIT License**. See the `LICENSE` file for details.
