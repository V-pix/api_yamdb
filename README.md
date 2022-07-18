# Групповой проект YaMDb

## Оглавление
- [Описание](#description)
- [Технологии](#technologies)
- [Запуск проекта](#launch)
- [Пользовательские роли](#users)
- [Ресурсы API YaMDb](#resources)

<a id=description></a>
## Описание
Групповой проект YaMDb для отзывов пользователей на произведения.
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий может быть расширен администратором. Сами произведения в YaMDb не хранятся. В каждой категории есть произведения: книги, фильмы или музыка. Произведению может быть присвоен жанр из списка предустановленных. Новые жанры может создавать только администратор. Пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти; из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.

Реализован REST API CRUD для моделей проекта, для аутентификации примненяется JWT-токен. В проекте реализованы пермишены, фильтрации, сортировки и поиск по запросам клиентов, реализована пагинация ответов от API, установлено ограничение количества запросов к API. 
### К API есть документация, доступная после запуска по адресу: `http://localhost:8000/redoc/`
---
<a id=technologies></a>
## Технологии
- Python 3.10
- Django REST Framework
- Simple JWT - работа с токеном
- Django-filter - фильтрация запросов
- PostgreSQL - база данных
- Git - система контроля версий

<a id=launch></a>
## Запуск проекта
### Клонировать репозиторий и перейти в него в командной строке:
```bash
git clone git@github.com:V-pix/api_yamdb.git
```
### Перейти в репозиторий в командной строке:
```bash
cd api_yamdb
```
### Cоздать виртуальное окружение:
```bash
python -m venv venv
```
### Активировать виртуальное окружение:
```bash
source venv/bin/activate        # для Linux
source venv/Scripts/activate    # для Windows
```
### Обновить pip:
```bash
python -m pip install --upgrade pip
```
### Установить зависимости из файла requirements.txt:
```bash
pip install -r requirements.txt
```
### Выполнить миграции:
```bash
python manage.py migrate
```
### Заполнить тестовые данные:
```bash
python manage.py importcsv
```
### Запустить проект:
```bash
python manage.py runserver
```

<a id=users></a>
## Пользовательские роли
- **Аноним** — может просматривать описания произведений, читать отзывы и комментарии.
- **Аутентифицированный пользователь (user)** — может, как и **Аноним**, читать всё, 
дополнительно он может публиковать отзывы и ставить оценку произведениям 
(фильмам/книгам/песенкам), может комментировать чужие отзывы; может редактировать 
и удалять свои отзывы и комментарии. Эта роль присваивается по умолчанию 
каждому новому пользователю.
- **Модератор (moderator)** — те же права, что и у **Аутентифицированного** 
пользователя плюс право удалять любые отзывы и комментарии.
- **Администратор (admin)** — полные права на управление всем контентом проекта. 
Может создавать и удалять произведения, категории и жанры. Может назначать 
роли пользователям.
- **Суперюзер Django** — обладает правами администратора (admin). Даже если 
изменить пользовательскую роль суперюзера — это не лишит его прав администратора. 
Суперюзер — всегда администратор, но администратор — не обязательно суперюзер.

<a id=resources></a>
## Ресурсы API YaMDb
- Ресурс auth: аутентификация.
- Ресурс users: пользователи.
- Ресурс titles: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).
- Ресурс categories: категории (типы) произведений («Фильмы», «Книги», «Музыка»).
- Ресурс genres: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.
- Ресурс reviews: отзывы на произведения. Отзыв привязан к определённому произведению.
- Ресурс comments: комментарии к отзывам. Комментарий привязан к определённому отзыву.
