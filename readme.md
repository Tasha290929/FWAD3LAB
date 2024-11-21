# Лабораторная работа №3. Основы работы с базами данных в Laravel

## Цель работы

Познакомиться с основными принципами работы с базами данных в Laravel. Научиться создавать миграции, модели и сиды на основе веб-приложения To-Do App.

### Условие

В данной лабораторной работе вы продолжите разработку приложения To-Do App для команд, начатого в предыдущих лабораторных работах.
Вы добавите функциональность работы с базой данных, создадите модели и миграции, настроите связи между моделями и научитесь использовать фабрики и сиды для генерации тестовых данных.

1. Создание моделей и миграций

```php
php artisan make:model Category -m
```

2. Определение структуры таблицы categories в миграции
Откройте файл миграции, созданный для categories (в каталоге database/migrations/) и добавьте следующие поля:

```php
public function up()
{
    Schema::create('categories', function (Blueprint $table) {
        $table->id(); // primary key
        $table->string('name'); // название категории
        $table->text('description')->nullable(); // описание категории
        $table->timestamps(); // created_at и updated_at
    });
}
```

3. Создание модели и миграции для Task

```php
php artisan make:model Task -m
```

4. Определение структуры таблицы tasks в миграции
Откройте файл миграции для tasks и добавьте нужные поля:

```php
public function up()
{
    Schema::create('tasks', function (Blueprint $table) {
        $table->id();
        $table->string('title'); 
        $table->text('description')->nullable(); 
        $table->timestamps(); 
    });
}
```

5. Создание модели и миграции для Tag
Выполните команду:

```php
php artisan make:model Tag -m
```

6. Определение структуры таблицы tags в миграции
Откройте файл миграции для tags и добавьте поля:

```php
public function up()
{
    Schema::create('tags', function (Blueprint $table) {
        $table->id(); 
        $table->string('name'); 
        $table->timestamps(); 
    });
}
```

7. Добавляем поле $fillable в модели Task, Category и Tag для массового заполнения данных.

8. Запустите миграцию для создания таблицы в базе данных:

```php
php artisan migrate
```

## №3. Связь между таблицами

Создайте миграцию для добавления поля category_id:


php artisan make:migration add_category_id_to_tasks_table --table=tasks