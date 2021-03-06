# 1. Перечень автоматизируемых сценариев

**Проверяемая функциональность:**
Приложение должно в собственной СУБД сохранять информацию о том, каким способом был совершён платёж и успешно ли он был совершён (при этом данные карт сохранять не допускается).
Все тесты делаем в двух вариантах, для блока "КУПИТЬ" и для блока "Купить в кредит"

**Карты, предоставленные для тестирования в файле data.json:**

4444 4444 4444 4441, status "APPROVED"

4444 4444 4444 4442, status "DECLINED"

**Характеристика вводимых валидных тестовых данных:**

поле "Номер карты": 16 цифр

поле "Месяц": двузначное числовое значение от 01 до 12

поле "Год": двузначное числовое значение;

поле "Владелец": допустимые значения из латинских букв, дефисов, пробелов

поле "CVC/CCV": три цифры


**1. Покупка с валидным номером карты:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год + 2"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Успешно! Операция одобрена банком". В БД статус операции: "APPROVED"*


**Негативные сценарии:**

**1. Покупка с невалидным номером карты:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4442".
2.	В поле "Год" ввести "Текущий год + 2"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Ошибка! Банк отказал в проведении операции"."Отказано". В БД статус операции: " DECLINED"*


**2.Попытка отправки формы с пустыми полями :**

1.	Оставить все поля пустыми
2.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибках под всеми полями. Форма не отправлена.*


**3. Отправки формы с пустым полем "Номер карты" :**
1.	Поле "Номер карты" оставить пустым.
2.	В поле "Год" ввести "Текущий год + 3"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Номер карты" отображается сообщение "Поле обязательно для заполнения"*


**4. Отправки формы с пустым полем "Год":**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441".
2.	Поле "Год" оставить пустым.
3.	В поле "Месяц" ввести "Текущий месяц + 3"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Год" отображается сообщение "Поле обязательно для заполнения"*


**5. Отправки формы с пустым полем "Месяц":**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441".
2.	В поле "Год" ввести "Текущий год + 3"
3.	Поле "Месяц" оставить пустым
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Месяц" отображается сообщение "Поле обязательно для заполнения"*


**6. Отправки формы с пустым полем "Владелец":**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441”
2.	В поле "Год" ввести "Текущий год + 3"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	Поле "Владелец" оставить пустым
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Владелец" отображается сообщение "Поле обязательно для заполнения"*


**7. Отправки формы с пустым полем "CVC/CVV":**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441".
2.	В поле "Год" ввести "Текущий год + 3"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	В поле "Владелец" вводятся данные Faker
5.	Поле "CVC/CVV" оставить пустым
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "CVC/CVV" отображается сообщение "Поле обязательно для заполнения"*


**8. Валидация поля "Владелец":**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год + 5"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	В поле "Владелец" вводятся данные Faker Ru
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "Владелец" отображается сообщение "Неверный формат"*


**9. Валидация поля "CVC/CVV":**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год + 3"
3.	В поле "Месяц" ввести "Текущий месяц + 2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" ввести "000"
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: В поле "CVC/CVV" отображается сообщение "Неверный формат"*


**10. Покупка с карты с истекшим сроком действия:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441".
2.	В поле "Год" ввести "Текущий год - 2"
3.	В поле "Месяц" ввести "Текущий месяц"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" ввести "123"
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Истёк срок действия карты" под полем "Год". Форма не отправлена.*

**11. Покупка с карты с истекшим сроком действия (в предыдущем месяце) :**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год"
3.	В поле "Месяц" ввести "Текущий месяц - 1"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Неверно указан срок действия карты" под полем "Месяц". Форма не отправлена.*


**12. Покупка с указанием неверного формата поля Номер карты:**
1.	В поле "Номер карты" ввести "4444 4444 4444"
2.	В поле "Год" ввести "Текущий год +3"
3.	В поле "Месяц" ввести "Текущий месяц +2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибке под полем "Номер карты" , форма не отправлена.*

**13. Покупка с указанием неверного формата поля Год:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "55"
3.	В поле "Месяц" ввести "Текущий месяц +2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибке под полем "Год" , форма не отправлена.*


**14. Покупка с указанием неверного формата поля Месяц:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год +3"
3.	В поле "Месяц" ввести "25"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибке под полем "Месяц" , форма не отправлена.*

**15. Покупка с указанием неверного формата поля Владелец:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год +3"
3.	В поле "Месяц" ввести "Текущий месяц +2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" ввести "12"
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибке под полем "Владелец" , форма не отправлена.*


**16. Покупка с указанием неверного формата поля CVC/CVV:**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год +3"
3.	В поле "Месяц" ввести "Текущий месяц +2"
4.	В поле "Владелец" ввести "32323 3232"
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление об ошибке под полем "CVC/CVV" , форма не отправлена.*



**17. Покупка с несуществующим номером карты:**
1.	В поле "Номер карты" ввести "0000 0000 0000 0000"
2.	В поле "Год" ввести "Текущий год +3"
3.	В поле "Месяц" ввести "Текущий месяц +2"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Ошибка! Банк отказал в проведении операции"."Отказано".


**18. Покупка с нулями в поле "Год"**
1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "00"
3.	В поле "Месяц" ввести "Текущий месяц"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Истёк срок действия карты" под полем "Год". Форма не отправлена.*


**19. Покупка с нулями в поле "Месяц"**

1.	В поле "Номер карты" ввести "4444 4444 4444 4441"
2.	В поле "Год" ввести "Текущий год"
3.	В поле "Месяц" ввести "00"
4.	В поле "Владелец" вводятся данные Faker
5.	В поле "CVC/CVV" вводятся данные Faker
6.	Нажать кнопку "Продолжить"

*Ожидаемый результат: уведомление "Неверно указан срок действия карты" под полем "Месяц". Форма не отправлена.*


# 2 Перечень используемых инструментов с обоснованием выбора

* **Java 11** - язык программирования
* **IntelliJ IDEA Ultimate Editor** - интегрированная среда разработки
* **Gradle** - система управления зависимостями
    - **Lombok** - Библиотека Lombok для генерации кода
    - **JavaFaker** -библиотека для генерации тестовых данных
* **JUnit Jupiter** - для запуска авто-тестов
* **Selenide** - Фреймворк для написания автотестов и их поддержки
* **Docker&DockerCompose** - система контейнеризации приложений. Выбрана с целью экономии ресурсов хостовой машины
* **Allure** - для генерации подробных отчетов о прохождении авто-тестов
* **GitHub** - веб-сервис для хостинга проекта тестирования и его совместной разработки
* **База данных SQL** – использование системы сборки и библиотеку для построения отчётов

# 3 Перечень и описание возможных рисков при автоматизации

• Отсутствие документации по описанию работы приложения

•	Сложности с первым запуском SUT и БД из-за недостатка знаний

•	Увеличение времени работы из-за недостаточной мощности ПК

•	Увеличение стоимости работы из-за увеличения времени

•	При изменении полей, текста, заголовков и т.д. тесты необходимо будет редактировать - сложность в поддержке актуального состояния тестов

# 4 Интервальная оценка с учётом рисков

•	Подготовка проекта, изучение тех.задания, установка программного обеспечения, запуск SUT - 8ч.

•	Написание плана тестирования - 8ч.

•	Написание тестов - от 24ч до 96ч.

•	Написание отчетов о тестировании - 8ч.

•	Написание отчетов об автоматизации - 6ч.

# 5 План сдачи работ

•	Написание плана тестирования - 1 день

•	Написание автотестов - от 15 до 20 дней после согласования плана тестирования -> 20.07.2022

•	Написание отчетов о тестировании и автоматизации - 1 день после написания автотестов -> 27.07.2022
