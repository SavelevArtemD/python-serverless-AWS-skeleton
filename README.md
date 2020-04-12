# Очередной склет для построения python приложений в AWS

### Основные фрэймворки:
- serverless
- pynamodb
- marshmallow
- structlog

### Что есть в этом скелете:   
- serverless.yml.   
Самые основы. Создание роли для деплоя и роли для исполнения лямбд. В плагинах 
есть warmap, если не нужен - удалите. В блок `functions:` офисываете свои лямбды и можетедеплоить.

- Настроенный логгер.   
Используется structlog, сконфигурирован на режим DEBUG если нужно будет легко измените, 
файл конфигурации: `services/logging.py` 

- Настроенный формат наименования таблиц DynamoDB.  
Предполагается использование базового класса для описания таблиц.
Так же по мере необходимости легко изменить, файл: `applications/base/base_db_model.py`

- Для лямбд реализован абстрактный класс `LambdaBase`   
Подход class-based lambda оказался удобен для применения паттерна inject. Файл:
`applications/base/base_lambda.py`

- Реализована базовая схема marshmallow

### Как пользоваться:
1. `git clone`
2. `npm i`
3. Настраивате интерпритатор и устанавливаете зависимости из `requirements.txt`
4. Для деплоя: `./deploy.sh <stage> <your_aws_profile>`
