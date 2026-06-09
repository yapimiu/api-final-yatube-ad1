"Апи социальной сети Yatube" (api_final)
1. Описание
2. Установка
3. Создание виртуального окружения
4. Команды для запуска
5. Примеры запросов к api
API для проекта социальной сети блогеров Yatube, на котором пользователи могут:

регистрироваться
создавать посты и управлять ими (корректировать\удалять)
создавать свои комментарии к постам и управлять ими (корректировать\удалять)
просматривать посты других пользователей
подписываться на других пользователей
2. Установка
Перед запуском необходимо склонировать проект:

[https://github.com/zizkinaziza-sketch/api-final-yatube-ad](https://github.com/zizkinaziza-sketch/api-final-yatube-ad)
cd api_final_yatube-ad/
3. Создание виртуального окружения
Cоздать и активировать виртуальное окружение:

python -m venv venv
Linux: source venv/bin/activate
Windows: source venv/Scripts/activate
4. Команды для запуска
И установить зависимости из файла requirements.txt:

python3 -m pip install --upgrade pip
pip install -r requirements.txt
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py runserver
Проект использует базу данных sqlite3.

5. Примеры запросов к api
Аутентификация

Выполнить POST-запрос http://localhost:8000/api/v1/jwt/create/ передав поля username и password.

Получить от API JWT-токен в формате:

{
  "refresh": "xxx",
  "access": "xxx"
}
В поле access вернётся токен. Данные в поле refresh будут необходимы для обновления токена.

При отправке запроcов передать токен в заголовке Authorization: Bearer <токен>.

Примеры запросов:
Результат POST-запроса с токеном пользователя на добавление нового поста:

Пример запроса:
{
    "text": "Текст",
    "group": 1
}
Пример ответа:
{
    "id": 1,
    "text": "Текст",
    "author": "Имя",
    "image": null,
    "group": 1,
    "pub_date": "2022-05-11T08:47:10.084572Z"
}
