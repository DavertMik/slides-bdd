
## Статус проекта

* комплексная доменная модель
* формализация требований
* сценарии взаимодействия

---

## Feature File

```gherkin
Feature: Plumbus
  In order to get a plumbus
  As a plumbus factory manager
  I need to create it via web interfce
```
Написано в языке Gherkin ↑



---

```gherkin
Scenario: Make Plumbus

Given first they take the dinglebop
And they smooth it out with a bunch of schleem
And the schleem is then repurposed for later batches

Then they take the dinglebop
And they push it through the grumbo where the fleeb is rubbed 
  against it

Given It is important that the fleeb is rubbed 
  because the fleeb has all of the fleeb juice
```

![](resources/shleem.jpg)

---

```gherkin
Then a schlami shows up
And he rubs it
And spits on it

Then they cut the fleeb
Given there are several hizzards in the way

Then the blamfs rub against the chumbles
And the ploobis and grumbo are shaved away

Then that leaves you with a regular old plumbus
```
![](resources/shlami.jpg)

---

### Текущий Сценарий

* записан слово в слово
* не хватает примеров
* не хватает конкретных значений

---

### Вопросы

* сколько нужно дингельбопа?
* откуда его взять?
* сколько нужно шлима?
* что делать, если шлим закончился?
* что происходит, если флиб не разрублен?
* что делать, если шлами заболел?
* **ЗАЧЕМ НУЖЕН ПЛЮМБУС???**

---

### Сценарий

```gherkin
Scenario: make plumbus
  Given we have a shalmi
  And "30" pounds of dinglebop
  And "2" pounds of shleem
  ...
  When we smooth out dinglebop with a schleem
  And we push it through the grumbo
  And shlamy rubs and spits on it
  ...
  Then we have regular old plumbus
```

---

### Сценарий

```gherkin
Scenario: make plumbus

Scenario: make plumbus without shlami and fail

Scenario: make plumbus reusing old shleem  

```

---

## Реализация

* Неужели мы сможем сделать это в РНР?
* Мы же профессионалы!

---

```php
class PlumbusFactory {
  public function make()
  {
    $dinglebop = new DingleBop();
    // re-purpose schleem
    try {
        $this->_schleem = $this->_blamf
            ->smoothDinglebopWithSchleem($dinglebop, $this->_schleem);
    } catch (OutOfSchleemException $e) {
        $this->_schleem = $this->_blamf
            ->smoothDinglebopWithSchleem($dinglebop, new Schleem());
    }
    $grumbo = new Grumbo();
    $grumbo->push($dinglebop);
    $this->_blamf->rubDinglebopWithFleeb($grumbo->dinglebop, $this->_fleeb);
    $this->_schlami->rubDingleBop($grumbo->dinglebop);
    $this->_schlami->spitOnDingleBop($grumbo->dinglebop);
    $this->_blamf->cutFleeb($this->_fleeb);
    $this->_blamf->rubAgainstTheChumbles($grumbo);
    $this->_blamf->shavePloobis($grumbo);
    return new Plumbus($this->_blamf->shaveGrumboAway($grumbo));
  }
```

---

### Тест

```php
public function testPlumbus() {
  $this->_dinglebop
    ->method( 'isPlumbusable' )
    ->willReturn( true );
  $plumbus = new Plumbus( $this->_dinglebop );
  $this->assertInstanceOf( Plumbus::class, $plumbus );
} // plumbus
```

---

## Вопросы

* что проверяет этот тест?
* как он связан со сценарием взаимодействия?
* важен ли он?
* нужен ли он?

---

## Behavior Testing

* Scenario == Test
* Шаг из User Story = шаг из теста
* Example == Specific Test

---

```php
/**
 * @Given we have a shalmi
 */
public function haveShlami()
{
  $this->shlami = new Shlami;
}

/**
 * @When shlamy rubs and spits on it
 */
public function shlamyActions()
{
  $this->shlami->spitOnDingleBop($this->product);
  $this->shlami->rubDingleBop($this->product);
}
```

---

## BDD и тестирование

* Позволяет делать значимые тесты
* Вся команда знает что делает тест
* Заказчик видит текущую работоспособность системы


---


#### Паттерны и антипаттерны

* **Плохо**: Тест ⇒ Спецификация
* **Хорошо**: Спецификация ⇒ Тест

---

## Плохо

```gherkin
Scenario: go through the service to button "Купить"

  Given open mysite.com
  When press button with text "Вход в кабинет"
  And type to input with name "userName" and text "vasya"
  And type to input with name "password" and text "1111"
  And press element with value "Войти
```

---


### BDD - all in one

* спецификация
* разработка
* тестирования

