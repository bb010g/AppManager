---
prev: ./
next: ./adb
sidebarDepth: 2
---

# Компоненты приложения

::: details Таблица содержания
[[toc]]
:::

## Что такое компоненты приложения?
Активити, службы, широковещательные приемники (также известные как приемники) и поставщики контента (также известные как поставщики) вместе называются компонентами приложения. Технически, все они наследуют класс `ComponentInfo`.

## Что такое трекеры?
_Трекер_ — это специальное ключевое слово в AM которое используется для обозначения рекламы или отслеживающего компонента. Она не обозначает количество реальных трекеров, как на странице [сканера](../guide/scanner-page.md). Это аналогично компоненту _трекера_ (в отличие от _классов трекеров_).

## Как блокируется трекер или другие компоненты в AM? Каковы его ограничения?
AM блокирует компоненты приложения (или компоненты трекера) с использованием метода под названием [Intent Firewall][1] (IFW), который очень превосходит другие методы, такие как `pm`, [Shizuku][5] или любой другой метод, использующий менеджер пакетов для включения или отключения компонентов. Если компонент отключен последними методами, само приложение может обнаружить, что компонент заблокирован и может снова его включить, так как оно имеет полный доступ к своим компонентам. (Множество мошеннических приложений на самом деле пользуются этим, чтобы разблокировать компоненты трекера.) С другой стороны, IFW - это настоящий брандмауэр, и приложение не может определить, присутствует ли блокировка. Оно также не может повторно включить заблокированый компонент никаким образом. AM использует термин _блокировать_, а не _отключить_ по этой причине.

Но даже у IFW есть некоторые ограничения, которые в первую очередь касаются системных приложений:
- Соответствующее приложение внесено системой в белый список, т.е. система не может работать должным образом без этих приложений, и это может вызвать случайные сбои. Эти приложения включают, но не ограничиваются системой Android, системным интерфейсом, телефонными службами. Они будут запущены, даже если вы отключите их или заблокируете их компоненты через IFW.
- Другое системное приложение или системный процесс вызывает конкретный компонент приложения через межпроцессное взаимодействие (IPC). В этом случае компонент будет активирован, независимо от его присутствия в правилах IFW, или даже если будет отключено всё приложение. Если у вас есть такие системные приложения, единственный способ запретить их работу - избавиться от них.

## Почему компоненты, заблокированные с помощью AM, не распознаются другими связанными приложениями?
Это происходит из-за метода блокировки, который я использую. Этот метод называется [Intent Firewall][1] (IFW) и он совместим с [Watt][2] и [Blocker][3]. [MyAndroidTool][4] (MAT) поддерживает IFW, но использует другой формат. Поэтому Watt по умолчанию может обнаружить заблокированные компоненты, а Blocker может их обнаружить, только если вы включите IFW на странице настроек. MAT не может обнаружить правила блокировки AM, так как формат различен. AM не может определить правила MAT, если IFW включен в MAT. В этом случае вы можете импортировать их из [страницы «Настройки»][9]. МАТ имеет опцию экспорта, но она не поддерживается из-за ее несвободного характера.

## Сохраняются ли в AM компоненты приложения, заблокированные другими инструментами?
**Нет.** Но компоненты, заблокированные системой Android или любыми другими инструментами, отображаются на странице [«Сведения о приложении»][10] (во вкладке компонентов). Начиная с версии 2.5.12, вы можете импортировать эти правила в [настройках приложения][9]. Но поскольку нет возможности отличить компоненты, заблокированные сторонними приложениями, от компонентов, заблокированных системой, вы должны быть очень осторожны при выборе приложения.

## Что бывает с компонентами, заблокированными с помощью AM, которые также заблокированы другими утилитами?
AM повторно блокирует компоненты, используя [Intent Firewall][1] (IFW). Они не будут разблокированы и снова заблокированы (если заблокированы с помощью метода _pm_ или [Shizuku][5]). Но если вы разблокируете компонент на странице [Сведения о приложении][6], он будет возвращен в состояние по умолчанию - заблокирован или разблокирован, как описано в соответствующем манифесте приложения - с использованием как IFW, так и метода _pm_. Однако компоненты, заблокированные с помощью [MyAndroidTools][4] (MAT) методом IFW не будет разблокирован AM. Чтобы решить эту проблему, вы можете сначала импортировать соответствующую конфигурацию в [настройках AM][9]. В этом случае конфигурации MAT будут удалены. Однако эта опция доступна только с версии 2.5.12.

## Что такое глобальная блокировка компонентов?
Когда вы блокируете компонент на странице [«Сведения о приложении»][6], блокировка не применяется по умолчанию. Применяется она только тогда, когда вы применяете блокировку с помощью опции _применить правила_ в правом верхнем меню. Если вы включите _глобальную блокировку компонентов_, блокировка будет применена, как только вы заблокируете компонент. Однако, если вы решите заблокировать компоненты трекера, блокировка применяется автоматически независимо от этого параметра. Вы также можете снять блокировку приложения, просто нажав на _удалить правила_ в том же меню на странице **«Сведения о приложении»**. Поскольку поведение по умолчанию дает вам больший контроль над приложениями, лучше оставить _глобальную блокировку компонентов_ выключенной.

_Смотрите также: [Глобальная блокировка компонентов][7]_

## Класс трекера и компоненты трекера, в чем разница?
Все компоненты приложения являются классами, но не все классы являются компонентами. По сути, лишь несколько классов являются компонентами. При этом [страница сканера][scanner] отображает список трекеров вместе с количеством классов, а не только компоненты. На всех других страницах трекеры и компоненты трекера используются как синонимы для обозначения компонентов трекера, то есть блокируются компоненты трекера, а не классы трекера.

::: tip Информация
Классы трекера не могут быть заблокированы. Они могут быть удалены только редактированием самого приложения.
:::

## Как разблокировать компоненты трекера, заблокированные с помощью Операции в один клик или пакетных операций?
Некоторые приложения могут работать некорректно из-за их зависимости от компонентов трекера, заблокированных с помощью AM. Начиная с версии 2.5.12, есть возможность разблокировать компоненты трекеров на странице [«Операции в один клик»][8]. Однако в предыдущих версиях таких вариантов нет. Чтобы разблокировать эти компоненты трекера, сначала перейдите на страницу [«Сведения о приложении»][6] некорректно функционирующего приложения. Затем переключитесь на вкладку _активити_, нажмите на кнопку _удалить правила_ в верхнем правом меню. Все правила блокировки, относящиеся к компонентам приложения, будут немедленно удалены. В качестве альтернативы, если вы нашли компонент, вызывающий проблему, вы можете разблокировать компонент, нажав на кнопку _разблокировать_ рядом с названием компонента. Если вы включили _глобальную блокировку компонентов_ в настройках приложения, сначала отключите ее, так как кнопка _Удалить правила_ не будет отображаться, когда блокировка включена.

Если на вашем устройстве установлены **Сервисы Google Play** (`com.google.android.gms`), разблокировка следующих [служб][services] может решить проблему:
- **Ad Request Broker Service**<br /> `.ads.AdRequestBrokerService`
- **Cache Broker Service**<br /> `.ads.cache.CacheBrokerService`
- **Gservices Value Broker Service**<br /> `.ads.GservicesValueBrokerService`
- **Advertising Id Notification Service**<br /> `.ads.identifier.service.AdvertisingIdNotificationService`
- **Advertising Id Service**<br /> `.ads.identifier.service.AdvertisingIdService`

[1]: https://carteryagemann.com/pages/android-intent-firewall.html
[2]: https://github.com/tuyafeng/Watt
[3]: https://github.com/lihenggui/blocker
[4]: https://www.myandroidtools.com
[5]: https://github.com/RikkaApps/Shizuku
[6]: ../guide/app-details-page.md
[7]: ../guide/settings-page.md#гnобаnьная-бnокировка-компонентов
[8]: ../guide/one-click-ops-page.md
[9]: ../guide/settings-page.md#импортирование-существующих-правиn
[10]: ../guide/app-details-page.md#цветовые-коды
[services]: ../guide/app-details-page.md#сnужбы
[scanner]: ../guide/scanner-page.md
