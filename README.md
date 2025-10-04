# API для управления задачами

### Структура методов API

- Создание задачи  
  POST /tasks  
  Описание: Создает новую задачу.  

  Пример запроса:  tasks?title=Test&description=Testapi&status=pending
  
  Ответ:  
  
```json
{
    "id": 6,
    "title": "Test",
    "description": "Testapi",
    "status": "pending",
    "created_at": "2025-10-04 13:00:00",
    "updated_at": "2025-10-04 13:00:00",
}
```
<hr>

- Просмотр списка задач  
  GET /tasks  
  Описание: Возвращает все задачи.  

  Пример запроса:  GET /tasks  

  Ответ:  
  
```json
  [
    {
      "id": 1,
      "title": "Test",
      "description": "Testapi",
      "status": "pending",
      "created_at": "2025-10-04 13:00:00",
      "updated_at": "2025-10-04 13:00:00",
    },
    {
    "id": 2,
    "title": "Test2",
    "description": "Testapi2",
    "status": "pending",
    "created_at": "2025-10-04 13:00:00",
    "updated_at": "2025-10-04 13:00:00",
    },
    {
    "id": 3,
    "title": "Test3",
    "description": "Testapi3",
    "status": "pending",
    "created_at": "2025-10-04 13:00:00",
    "updated_at": "2025-10-04 13:00:00",
    }
  ]
```

<hr>

- Просмотр одной задачи  
  GET /tasks/{id}  
  Описание: Возвращает задачу по её ID.
  Пример запроса: /tasks/{3}

  Ответ:  
  
```json
{
    "id": 3,
    "title": "Test3",
    "description": "Testapi3",
    "status": "pending",
    "created_at": "2025-10-04 13:00:00",
    "updated_at": "2025-10-04 13:00:00",
}
```
<hr>

- Обновление задачи  
  PUT /tasks/{id}  
  Описание: Обновляет информацию о задаче.  
  Тело запроса:  
  
```json
{
    "title": "New Title",
}
```
  
  
  Ответ:  
  
```json
{
    "id": 1,
    "title": "New Title",
    "description": "Testapi",
    "status": "pending",
    "created_at": "2025-10-04 13:00:00",
    "updated_at": "2025-10-04 13:00:00",
}
```
<hr>

- Удаление задачи  
  DELETE /tasks/{id}  
  Описание: Удаляет задачу по её ID. 

  Ответ:  
  
```json
  {
    "message": "Task deleted successfully"
  }
```
<hr>

### Правила валидации

| Поле          | Правила валидации (Добавление)                    | Правила валидации (Редактирование)                    | Описание                                    |
|---------------|---------------------------------------------------|-------------------------------------------------------|---------------------------------------------|
| `title`       | `required\|string\|max:255`                       | `sometimes\|required\|string\|max:255`                | Заголовок задачи                            |
| `description` | `required\|string`                                | `sometimes\|required\|string`                         | Описание задачи                             |
| `status`      | `required\|in:pending, completed`                 | `sometimes\|required\|in:pending, completed`          | Статус задачи                               |

<hr>

### Тестирование
- Тестирование функционала проводилось в программе Postman. Скриншоты с примерами запросов и результатами находятся в директории <b>/ScreenTests/</b>
    <hr>
### Файлы с реализацией
- /taskapilaravel.local/routes/api.php
- /taskapilaravel.local/app/Models/Task.php
- /taskapilaravel.local/app/Http/Requests/TaskStoreRequest.php
- /taskapilaravel.local/app/Http/Requests/TaskUpdateRequest.php
- /taskapilaravel.local/app/Http/Resources/TaskResource.php
- /taskapilaravel.local/app/Http/Controllers/TaskController.php
- /taskapilaravel.local/database/migrations/2025_02_28_185637_create_tasks_table.php
- /taskapilaravel.local/database/factories/TaskFactory.php
- /taskapilaravel.local/database/seeders/TaskSeeder.php