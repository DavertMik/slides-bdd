## Codeception

* Full stack testing framework
* Поддерживает популярные PHP фреймворки
* Тестирование UI через WebDriver
* Поддержка Gherkin (с версии 2.2)

---

## Почему BDD с Codeception

* встроенные инструменты:
  * Selenium тестирование
  * тестирование БД
  * тестирование фреймворков
  * тестирование очередей
* множество форматов (Unit, Gherkin, Cest)

---

## Тест != Feature

* Не все тесты - часть спецификации
* Баги не являются спецификацией
* Описание всех возможных сценариев в Gherkin добавляет информационный шум

---

## Features ∈ Tests

* Feature описывают предполагаемые сценарии
* Regression test описывает проблемные сценарии
* Regression test `@depends` on Feature

---

## Как работать?

* размещаем спецификации в features
* делаем symlink с features ⇒ tests/{тип теста}
* пишем сценарные шаги для каждого вида тестов

---

## Типы тестов

* Functional - без UI, но с фреймворком
```
  ln -s $PWD/features ⇒ tests/functional
```
* Unit - компоненты системы
```
  ln -s $PWD/features ⇒ tests/unit
```

* Acceptance - UI + WebServer 
```
  ln -s $PWD/features ⇒ tests/acceptance
```

---

## Работаем!

* Пишем спецификации!
* Пишем тесты!
* Делаем плюмбусы!

![](resources/happy.jpg)

---

## Спасибо!

Михаил Боднарчук @davert

* Codeception BDD Guide [codeception.com/docs/07-BDD](http://codeception.com/docs/07-BDD)
* Plumbus-PHP [github.com/remotelyliving/plumbus-php](https://github.com/remotelyliving/plumbus-php)
* Liz Keogh: BDD [lizkeogh.com/behaviour-driven-development/](https://lizkeogh.com/behaviour-driven-development/)
* Dan North: What's in a Story [dannorth.net/whats-in-a-story/](https://dannorth.net/whats-in-a-story/)