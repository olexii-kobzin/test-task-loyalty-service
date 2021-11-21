# Loyalty Service

В репозитории находится реализация микро-сервиса, который отвечает за работу 
системы лояльности и может использоваться в розничной торговле или сфере услуг,
везде, где за какую либо операцию (продажу) можно начислить определённое 
количество баллов лояльности, а потом потратить эти баллы на оплату товаров/услуг.

Доступные операции:
- Начисление баллов лояльности за операцию (loyaltyPoints/deposit).
- Отмена начисления баллов за операцию (loyaltyPoints/cancel).
- Оплата покупки баллами лояльности (loyaltyPoints/withdraw).
- Получение текущего баланса по карте лояльности (накопленное количество баллов лояльности) (account/balance).

При начислении баллов лояльности необходимо указать правило начисления.

Правило начисления может быть:
- Относительным — количество начисляемых баллов лояльности рассчитывается как процент от суммы операции.
- Абсолютным — в независимости от суммы операции начисляется фиксированное количество баллов лояльности.

Задача:
1. Архив репозитория распаковать и опубликовать в публичный GIT-репозиторий.
2. В отдельной ветке необходимо провести рефакторинг приложения в соответствии с Best Practices, Вашими предпочтениями и опытом.
3. Оформить Pull/Merge Request на ветку с исходным заданием и передать ссылку рекрутеру.

Рекомендации:
1. Предоставить краткое описание выбранных архитектурных решений.
2. Детализировать историю изменений вместо одного итогового коммита.
3. Соблюдать общепринятые правила оформления кода, документации и истории изменений.
4. Не углубляться в детали реализации непринципиальных моментов.
5. Не тратить на задание больше 1-2 дней.

## Installation
### Prod
```shell
cd test-task-loyalty-service; docker-compose up
```
### Dev
```shell
cp docker-compose.override.yml.example docker-compose.override.yml;
cd test-task-loyalty-service;
docker-compose up
```
- Windows
```shell
docker run -it --user 1000 -v ${pwd}:/var/www test-task-loyalty-service /bin/sh -lc "composer install && cp .env.example .env && php artisan key:generate && php artisan migrate"
```
- Linux
```shell
docker run -it --user 1000 -v $PWD:/var/www test-task-loyalty-service /bin/sh -lc "composer install && cp .env.example .env && php artisan key:generate && php artisan migrate"
```
Stop running docker-compose.
Uncomment `command: "php artisan serve --host=0.0.0.0 --port=8000"`.
Run `docker-compose up`.

