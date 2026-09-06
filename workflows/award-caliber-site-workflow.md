**Response Header**  
- **Date:** 2026-09-06  
- **Author:** Creative Site Orchestrator (Skill 23)  
- **Version:** 1.0.0  
- **Project:** <PROJECT_NAME>  
- **Mode:** Plan / Build  

---  

## Decision Record / Project Knowledge Patch (PKP) Schema  

| Field                | Type    | Description |
|----------------------|---------|-------------|
| `record_id`          | string  | Unique identifier (e.g., `DR-2026-09-06-001`) |
| `timestamp`          | string  | ISO‑8601 datetime of the decision |
| `stage`              | string  | Workflow stage the decision belongs to |
| `decision`           | string  | Concise description of the decision |
| `rationale`          | string  | Why the decision was made (incl. trade‑offs) |
| `impact`             | string  | Expected effect on accessibility, performance, conversion |
| `approval`           | string  | Approver’s name / role |
| `next_steps`         | string  | Immediate actions required |
| `links`              | array   | References to artifacts, tickets, or external docs |

*Add a new record to `PROJECT_ROOT/.pkp/decisions.jsonl` after each approval gate.*  

---  

## План vs Build  

| Aspect | План (Plan) | Build |
|--------|-------------|-------|
| **Цель** | Определить что и как будет создаваться; сформировать артефакты‑спецификации, согласовать их с заинтересованными сторонами. | Реализовать спецификации в коде/контенте, проверять соответствие и готовить к выпуску. |
| **Выход** | Техническое задание, макеты, карта компонентов, критерии приемки. | Рабочий прототип, проверенный QA, готовый к масштабированию сайт. |
| **Ключевые действия** | Исследования, идеи, прототипы, согласования. | Верстка, интеграция, тестирование, оптимизация. |
| **Контроль качества** | Ревью концепций, чек‑лист доступности, производительности, конверсии. | Автоматические и ручные тесты, аудит доступности, нагрузочное тестирование. |
| **Риск** | Неправильные гипотезы → пере‑работа в Build. | Технический долг → падение метрик после релиза. |

---  

## Матрица стадий (одна стадия — один запрос)  

| Текущая стадия | Режим | Основной навык | Поддерживающие навыки | Артефакт | Шлюз одобрения |
|----------------|-------|----------------|----------------------|----------|----------------|
| **Project Truth** | План | 23 Creative Site Orchestrator | 05 Research, 12 Stakeholder Management | Документ «Project Truth» (цели, ограничения, KPI) | Руководитель проекта |
| **Big Idea** | План | 23 | 07 Ideation, 09 Brand Strategy | Концептуальный бриф + mood‑board | Бренд‑директор |
| **Visual World** | План | 23 | 08 UI Design, 11 Accessibility | UI‑kit, стилистика, цветовая палитра | Дизайн‑lead |
| **Experience/Interaction** | План | 23 | 10 UX Flow, 14 Interaction Design | Карты пользовательских сценариев, прототипы (Figma) | UX‑lead |
| **Asset System (if needed)** | План | 23 | 06 Content Architecture, 13 Asset Management | Схема управления медиа‑активами | Content‑manager |
| **Representative Slice plan** | План | 23 | 02 Scope Definition, 15 Roadmapping | План «Slice» (список страниц, функции) | PM |
| **Build Representative Slice** | Build | 23 | 03 Front‑end, 04 Back‑end, 16 Performance | Рабочий прототип «Slice» (HTML/CSS/JS) | Технический lead |
| **Independent Critique** | План | 23 | 18 Peer Review, 19 Accessibility Audit | Отчёт критики с рекомендациями | QA‑lead |
| **Fix P0/P1** | Build | 23 | 20 Bug Fixing, 21 Optimization | Исправленный «Slice», регрессионные тесты | QA‑lead |
| **Scale full site** | Build | 23 | 22 Modular Architecture, 24 CI/CD | Полный сайт (модульные компоненты) | Руководитель проекта |
| **Final QA/Release** | Build | 23 | 25 Release Management, 26 Monitoring | Финальный релиз‑пакет, чек‑лист QA | Руководитель проекта + заказчик |

*После каждой стадии добавляйте запись в Decision Record.*  

---  

## Готовые к копированию запросы (raw markdown)  

### 1. Запуск проекта (Project Kickoff)  

```
Начинаем проект **<PROJECT_NAME>**.  
Текущая стадия: Project Truth.  
Режим: План.  
Основной навык: Creative Site Orchestrator (23).  
Поддерживающие навыки: Research (05), Stakeholder Management (12).  
Создай документ «Project Truth» с целями, ограничениями, KPI и отправь на утверждение руководителю проекта.  
```

### 2. Перейти к следующей стадии  

```
Продолжаем проект **<PROJECT_NAME>**.  
Текущая стадия: <ТЕКУЩАЯ_СТАДИЯ>.  
Перейти к следующей стадии: <СЛЕДУЮЩАЯ_СТАДИЯ>.  
Подготовь необходимые артефакты согласно матрице и запроси одобрение у <ОТВЕТСТВЕННОГО>.  
```

### 3. Сборка одобренного Representative Slice  

```
Собираем Representative Slice для **<PROJECT_NAME>**.  
Текущая стадия: Build Representative Slice.  
Используй UI‑kit, прототипы и план Slice.  
Выдай рабочий прототип (HTML/CSS/JS) и запусти автоматические тесты.  
Отправь артефакт на проверку техническому lead.  
```

### 4. Аудит Slice (Independent Critique)  

```
Проводим независимый аудит Slice проекта **<PROJECT_NAME>**.  
Текущая стадия: Independent Critique.  
Сделай обзор с точки зрения доступности, производительности и конверсии.  
Сформируй отчёт с рекомендациями уровня P0/P1 и передай QA‑lead.  
```

### 5. Реализация исправлений (Fix P0/P1)  

```
Вносим исправления в Slice проекта **<PROJECT_NAME>**.  
Текущая стадия: Fix P0/P1.  
Исправь все критические (P0) и высокоприоритетные (P1) проблемы, проведи регрессионные тесты.  
Обнови артефакт и запроси повторный одобрительный чек‑лист у QA‑lead.  
```

### 6. Масштабирование полного сайта (Scale full site)  

```
Масштабируем сайт **<PROJECT_NAME>** до полной версии.  
Текущая стадия: Scale full site.  
Разверни все модули, настрой CI/CD, проведи нагрузочное тестирование.  
Подготовь релиз‑пакет и запроси окончательное одобрение у руководителя проекта и заказчика.  
```

---  

## Восстановление при неверном выборе навыка Lovable  

Если система **Lovable** ошибочно выбрала другой навык вместо **Creative Site Orchestrator (23)**:  

1. **Остановить** текущий процесс и зафиксировать ошибку в Decision Record (`record_id: DR-...-ERR01`).  
2. **Переключить** активный навык к 23 вручную:  
   ```
   set_active_skill 23
   ```  
3. **Повторить** последний запрос, указав явно нужный навык в начале (см. шаблоны выше).  
4. **Документировать** причину ошибки (неправильный контекст, конфликт зависимостей) и добавить в PKP рекомендацию по улучшению выбора навыков.  

---  

### Примечание по защите  

- **Доступность:** каждый артефакт проходит WCAG 2.2 AA‑аудит; любые отклонения фиксируются как P0.  
- **Производительность:** включены автоматические Lighthouse‑проверки; отклонения > 90 % score → блокировка перехода.  
- **Конверсия:** KPI‑трекинг (CTR, CR) задаётся в «Project Truth» и проверяется на каждом этапе.  
- **Клонирование:** запрещено копировать чужие UI‑компоненты без лицензии; все активы должны быть оригинальными или с открытой лицензией.  

*Готово к копированию в репозиторий GitHub.*
