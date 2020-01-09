# Обзор

Любой блокчейн должен обладать механизмом, позволяющим решить, какая цепочка блоков является главной, и гарантировать, что в ней не происходит двойной траты средств \(например, отправка одних и тех же денег различным сторонам в разных цепочках\). Существует несколько подходов к достижению этой цели.
Waves использует так называемый Proof-of-Stake алгоритм консенсуса (доказательство доли владения). Мы опишем его и сравним с широко используемым алгоритмом Proof-of-Work, который используется, например, в биткойне.

Так как каждый блокчейн представляет собой систему децентрализованных «нод» \(или компьютеров, подтверждающих транзакции, происходящие в сети, и поддерживающих децентрализованный консенсус всей системы\), наличие нод, или «майнеров» в Proof-of-Work или «валидаторов» в Proof-of-Stake (мы часто также используем слово понятие «майнеры», для отсутствия путаницы у участников), является важным для сохранения транзакций. Способ, которым ноды «майнеры» или «валидаторы» подтверждают транзакции и система поощрения нод - основные различия между Proof-of-Work и Proof-of-Stake.


# 1. Proof-of-Work \(PoW\) 

Proof-of-Work - алгоритм консенсуса, который требует для генерации блока выполнить трудозатратное вычисление (то есть произвести майнинг), чтобы создать новую группу доверенных транзакций \(так называемый блок\) в блокчейн.

Майнинг преследует две цели:

1. Создание цепочки блоков, которая может рассматриваться, как главная цепочка \(так как создание альтернативной цепочки является слишком ресурсозатратным\)

2. Майнинг новых монет \(повышение общего количества денежных средств в сети\) путем выдачи награды майнерам за выполнение задания.

**Когда вы хотите добавить транзакцию в блокчейн, вот что происходит за кадром:**

* Транзакции объединяются в блок.

* Майнеры подтверждают, что транзакции в блоке являются валидными.

* Майнеры должны решить некоторую трудоемкую математическую задачку, чтобы сгенерировать валидный блок (например, сгенерировать число, хэш от которого будет начинаться с конкретного числа нулей).

* Блок, появившийся в результате решения задачки признается валидным и транслируется на все ноды сети и отправляется в публичный блокчейн.

* Майнеру, который сумел первым сгенерировать такой блок, выдется награда за потраченные на решение задачки ресурсы.

Такая "математическая задачка" имеет ключевое требование: ассиметричность затрат на решение и проверку выполненной работы. Производимая работа должна быть достаточно сложной на стороне майнеров, но легко проверяться сетью. Эта идея также известна как функция клиентской головоломки, вычислительная головоломка или функция ценообразования CPU. Все майнеры сети конкурируют за первенство в решении математической задачи, которую необходимо решить для того чтобы быть кандидатом на генерацию блока и которая не может быть решена другими способами, кроме как с помощью "грубой силы" перебора. Когда майнер, находит правильное решение, он одновременно объявляет его всей сети, получая при этом криптовалютное вознаграждение, предоставляемое по протоколу.

«Атака 51%» относится к атакам на блокчейн и заключается в следующем: контролируя бОльшую часть вычислительной мощности сети, злоумышленник может создать форк и восстановить свои монеты, выполнив атаку «двойной траты», которая позволит проводить операции над его монетами по несколько раз. Нападавший может тратить монеты в одном месте, позволяя монетам входить в блокчейн как обычно до тех пор, пока не будут получены необходимые подтверждения, а затем запустит 51% майнеров для создания мошеннического форка, в котором эти монеты никогда не участвовали в операциях. Такую процедуру теоретически можно повторять до тех пор, пока атакующий хранит под своим контролем 51% вычислительной мощности сети.

Преимущество протокола Proof-of-Work заключается в том, что большая часть голосов при осуществлении важных изменений в системе делится между майнерами, разработчиками и другими значимыми членами сообщества. В то время, как в сети Proof-of-Stake, наиболее влиятельные игроки, с наибольшим количеством монет, имеют техническую возможность делать любые изменения, которые им нравятся, без учета мнения сообщества, бизнеса, майнеров и разработчиков.

Такая централизация полномочий в голосовании и контроль над сетью, казалось бы, нарушают цель распределенной криптовалюты на блокчейне, поскольку централизация противоречит принципу распределения всех элементов внутри сети.

## 1.1 Недостатки Proof-of-Work 

* Требуется больше электроэнергии, что, в свою очередь, приносит майнерам убытки.
* Оборудование с высокой вычислительной мощностью является дорогостоящим.
* Возможности майнеров перемещаться на другие монеты, если там их вычислительная мощность может принести им больше средств \(лояльности к конкретной монете в зависимость от типа требуемой работы\).
* С увеличением числа монет, вознаграждение майнера будет уменьшаться, так как монета становится скудной для осуществления майнинга.

# 2. Proof-of-Stake \(PoS\) 

Proof-of-Stake - это другой способ валидирования транзакций, основанный на распределенном консенсусе. Цель является такой же, как и у Proof-of-Work, но достигается совершенно иначе.

В PoW количество блоков майнера пропорционально количеству аппаратных мощностей и энергии, которые он вложил. В PoS-е же майнер может майнить или валидировать транзакции в блоке в соответствии с количеством монет, которые он держит. Таким образом, в отличие от Proof-of-Work, создатель нового блока выбирается практически случайным образом, при этом большее количество монет увеличивает вероятность майнера добавить блок в блокчейн.

Обычно в системе PoS нет вознаграждения за блок, поэтому майнеры берут комиссию за транзакции. Вот почему майнеров часто называют генераторами блоков, Рисунок 1.

При использовании PoS злоумышленнику необходимо будет получить 51% монет системы для атаки 51%. Доказательство владения избегает такой неприятной ситуации, делая ее невыгодной для майнера с 51%-ной долей. Хотя было бы сложно и дорого накапливать 51% цифровой монеты, майнер с 51%-ной долей монет системы не был бы заинтересован в атаке на сеть. Если ценность криптовалюты падает, это означает, что стоимость его вкладов также упадет, и поэтому владелец большинства монет будет скорее заинтересован в поддержания безопасности сети.

PoS содержит ограничения, для того, чтобы избежать некоторые виды атак:

* Минимальное количество WAVES для генерации - 1000 WAVES
* Когда баланс возрастает, генерирующий баланс возрастает только после 1000 блоков.

## 2.1 Почему мы используем Proof-of-Stake 

* Существенное преимущество Poof-of-Stake - отсутствие растраты энергии
* Waves реализует Proof-of-Stake метод для наиболее экологичного и дешевого способа организации распределенной системы.
* В Proof-of-Stake, те, кто генерирует блоки - всегда те, кто майнит монеты.

![](./_assets/PoW.png)Рисунок 1, PoW vs PoS

# 3. Leased Proof-of-Stake \(LPoS\) 

LPoS (дословно -  арендованное доказательство доли владения) - это улучшенная версия Proof-of-Stake. В обычной версии Proof-of-Stake,  каждая нода держит некоторое количество монет, чтобы иметь право сгенерировать следующий блок в блокчейне, но в LPoS системе Waves Platform, пользователи могут сдавать свои балансы в лизинг full-нодам. LPoS предоставляет пользователю возможность сдать WAVES в лизинг
формируя кошелек для других майнеров, которые могут выплачивать проценты от майнинга в качестве вознаграждения. Чем больше сумма, сдаваемая в аренду на full-ноду, тем выше вероятность того, что эта full-нода будет выбрана для создания следующего блока. Если эта full-нода выбрана для создания следующего блока, тогда лизингодатель получит процент от суммы транзакции, собираемой full-нодой.

В Leased Proof-of-Stake окружении, пользователи могут выбирать между запуском full-ноды и сдачей своих монет в лизинг другим full-нодам для получения вознаграждения. Эта система позволяет любому поучаствовать в поддержке сети Waves.

Пользователь может сдать свои средства в лизинг с компьютера или с мобильного девайса, для этого достаточно просто иметь браузер, так как Waves предоставляет легкую версию своего клиента, которая не требует у майнеров скачивания и хранения у себя всего блокчейна или запуска кошелька, Рисунок 2.

![](./_assets/Webp.net-resizeimage-2.jpg)  
Рисунок 2, LPOS система

## 3.1 Преимущества лизинга WAVES 

Безопасность \(ваши WAVES никогда не покидают ваш кошелёк\):

* Ноды используют ваши ресурсы для генерации блоков, не требуя перевода средств на свой баланс.
* Лизинг безопасен: ваши средства никогда не покидают ваш кошелёк.
* Пользователи могут прервать лизинг в одностороннем порядке, просто нажав кнопку и подождав отмены лизинга, Рисунок 2.
* Единственная вещь, которую стоит принять во внимание для успешного осуществления лизинга - выбор ноды оператора, так как все ноды имеют разную эффективность и от этого зависит доход от лизинга.

Минимальный баланс для запуска ноды:

* Операторы не должны иметь какой-то определенный, ограниченный снизу баланс для того чтобы стать оператором ноды.
* Баланс ноды может быть пустым до того, как люди захотят сдавать ей монеты в лизинг, главное совместно достичь генерирующего баланса в  1000 WAVES и создать совместный пулл.

Получение награды:

* Майнеры могут присылать лизингодателю часть награды за майнинг, согласно указанным ими условиям.
* Чем больше транзакций произошло в сети, тем большую награду получит лизингодатель.
* Награда обычно приходит в виде WAVES, но также может прийти в других токенах (до тех пор, пока действительна комиссия в токенах).

# 3.2 Транзакции лизинга 

## 3.2.1 Транзакция создания лизинга 

```
"Id": 9q7X84wFuVvKqRdDQeWbtBmpsHt9SXFbvPPtUuKBVxxr ,
"sender" : 3HgqG68qfeVz5dqbyvqnxQceFaH49xmGvUS ,
"fee" : 0.001,
"amount" : 10,
"recipient address" : 3HQanDJhZSsSLbCjTCsMYpPvuj2ieGwKwQ9"
"timestamp":46305781705234713
```

## 3.2.2 Транзакция отмены лизинга 

```
"sender" : 3HgqG68qfeVz5dqbyvqnxQceFaH49xmGvUS ,
"leaseId": 9q7X84wFuVvKqRdDQeWbtBmpsHt9SXFbvPPtUuKBVxxr
```

# 3.2.3 Полезные ссылки для лизинга 

Пошаговое руководство по сдаче средств в лизинг [здесь](/waves-client/account-management/waves-leasing).

Список нод генераторов [здесь](http://dev.pywaves.org/generators/).

Waves-ноды [здесь](https://wavesplatform.com/leasing#nodes).