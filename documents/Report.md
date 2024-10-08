# Отчет о проведенном тестировании
В проекте проведено автоматизированное тестирование сервиса по покупке тура, который взаимодействует с СУБД и API банка.
## Что было протестировано:
- Отправка формы при оплате по дебетовой карте
- Отправка формы при оплате с получением кредита по данным карты
- Валидация полей формы для данных банковской карты
- Отражение статуса платежа в базе данных
- Отражение суммы платежа в базе данных
- Ответ сервера при отправке данных банковской карты через POST-запрос
- Поддержка двух СУБД: MySQL, PostgeSQL.

## Статистика

Всего выполнено  автотестов, из них:

- Успешных -  (%)
- Неуспешных -  (%)

По итогам тестирования сформирован отчет Allure Report
### Общий отчет



### Отчет APITests



### Отчет OrderCreditTest



### Отчет OrderPaymentTest




## Общие рекоммендации

- Добавить ограничения для поля "Владелец": возможность ввода только латиницы в обоих регистрах и знаков препинания, которые могут использваться при написании имен и фамилий (апостроф, дефис и т.д)
- Добавить уведомление об отклонении платежа при вводе данных невалидной карты из тестовых данных (*4442)
- Добавить к элементам веб-страниц приложения атрибут "data-test-id" (или "name") для облегчения поиска элементов при написании автотестов в будущем
- Сервер должен уметь обрабатывать данные незнакомой карты и возвращать статус 400.
  Полный список найденных багов представлен в 