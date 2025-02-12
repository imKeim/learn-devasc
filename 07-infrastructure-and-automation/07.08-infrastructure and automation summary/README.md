<!-- 7.8.1 -->
## Что я узнал в этом модуле?

### Автоматизация инфраструктуры с помощью Cisco

Автоматизация использует код для настройки, развертывания и управления приложениями вместе с вычислительными ресурсами, хранилищами и сетевыми инфраструктурами и службами, на которых они работают. У вас есть выбор, как программно управлять конфигурациями сети и инфраструктурой. Прогулка: автоматизация только для чтения. Запуск: активация политик и предоставление самообслуживания в нескольких доменах. Fly: развертывание приложений, сетевых конфигураций и прочего с помощью CI/CD. Ручные процессы всегда подвержены человеческим ошибкам, а документация, предназначенная для людей, часто бывает неполной и неоднозначной, трудной для тестирования и быстро устаревает. Автоматизация - ответ на эти проблемы. Преимущества полной автоматизации - самообслуживание, масштабирование по запросу, наблюдаемость и автоматическое устранение проблем. Программно-определяемая инфраструктура, также известная как облачные вычисления, позволяет разработчикам и операторам использовать программное обеспечение для запроса, настройки, развертывания и управления «голыми» и виртуализированными вычислительными ресурсами, хранилищами и сетевыми ресурсами. Современные архитектуры приложений получают все большее распространение. Они состоят из небольших и относительно легких компонентов, которые иногда называют микросервисами.

### DevOps и SRE

Чтобы полная автоматизация была действительно эффективной, необходимы изменения в организационной культуре, в том числе устранение исторического разрыва между разработкой (Dev) и операциями (Ops). DevOps развивалась и продолжает развиваться во многих местах параллельно. Некоторые ключевые события сформировали дисциплину, которую мы знаем сегодня.

Определяющие моменты 1: Проектирование надежности площадки (SRE). Роль SRE предназначена для объединения дисциплин и навыков разработчиков и операторов.

Определяющие моменты 2: Дебуа и «гибкая инфраструктура» Дебуа был сторонником автоматизации виртуальной инфраструктуры, использования контроля версий для хранения кода развертывания инфраструктуры и применения гибких методов для разработки и обслуживания решений на уровне инфраструктуры.

Определяющие моменты 3: Олспоу и Хаммонд

Джон Олспоу и Пол Хэммонд выступили с презентацией на VelocityConf в 2009 году. В ней описывались автоматизация, командная работа, разделение ответственности, прозрачность, доверие, взаимная подотчетность и методы коммуникации.

DevOps/SRE имеют множество основных принципов и лучших практик:

* Акцент на автоматизацию
* Идея о том, что «неудача - это нормально»
* Переосмысление «доступности» с точки зрения того, что может терпеть бизнес.

### Базовые сценарии автоматизации

Инструменты автоматизации частично работают путем обертывания функций оболочки, служебных программ операционной системы, функций API и других элементов плоскости управления. Но инструменты по-прежнему не решают всех проблем развертывания и настройки. Вот почему каждый инструмент автоматизации имеет одну или несколько функций, которые выполняют базовые команды и сценарии для целей и возвращают результаты. Например, в Ansible эти функции включают command, shell и raw. Такие инструменты автоматизации, как Ansible, Puppet или Chef, предлагают мощные возможности по сравнению со специальными стратегиями автоматизации с использованием BASH, Python или других языков программирования. Императивная процедура - это упорядоченная последовательность команд, направленных на достижение цели. Последовательность может включать в себя управление потоком, условия, функциональную структуру, классы и многое другое. Чтобы настроить удаленные системы, вам необходимо получить доступ к ним и выполнить на них скрипты. `scp`, затем войдите на удаленный компьютер, используя `ssh` и казни их. Или вы можете передать скрипты на удаленный компьютер, используя `cat | ssh` и выполнять их последовательно с другими командами, собирая и возвращая результаты на ваш терминал, все в одной команде. Инфраструктура облачных вычислений «Инфраструктура как услуга» (IaaS) является типичной целью для автоматизации. Автоматизация облака позволяет вам предоставлять виртуализированные хосты, настраивать виртуальные сети и другие возможности подключения, запрашивать услуги, а затем развертывать приложения в этой инфраструктуре. IaaS и другие типы облачной инфраструктуры также предоставляют интерфейсы командной строки и SDK, которые позволяют легко подключаться к их базовым интерфейсам, которые обычно основаны на REST.

### Инструменты автоматизации

Три самых популярных инструмента автоматизации - это Ansible, Puppet и Chef. Такие инструменты автоматизации, как Ansible, Puppet или Chef, предлагают мощные возможности по сравнению со специальными стратегиями автоматизации с использованием BASH, Python или других языков программирования. Идемпотентное программное обеспечение дает один и тот же желаемый результат при каждом запуске. В программном обеспечении для развертывания идемпотентность обеспечивает конвергенцию и компоновку. Процедурный код может достигать идемпотентности, но многие инструменты управления инфраструктурой, развертывания и оркестровки используют другой метод, который создает декларативное. Декларативная - это статическая модель, представляющая желаемый конечный продукт.

Базовая архитектура Ansible очень проста и легка. Узел управления Ansible работает практически на любой машине Linux, на которой работает Python 2 или 3. Все обновления системы выполняются на узле управления. Плагины позволяют Ansible собирать факты и выполнять операции в инфраструктуре, которая не может запускать Python локально, например в интерфейсах REST облачного провайдера. В значительной степени Ansible управляется из командной строки Bash, а код автоматизации разрабатывается и поддерживается с помощью любого стандартного текстового редактора.

Основная архитектура Puppet имеет следующие характеристики: выделенный сервер для размещения основных компонентов приложения, называемый Puppet Server, Facter, который является службой сбора фактов, PuppetDB, который может хранить факты, каталоги узлов и историю недавних событий конфигурации, а также безопасный клиент, агент Puppet, установленный и настроенный на целевых машинах. Операторы общаются с Puppet Server в основном через SSH и командную строку.

Основными компонентами Chef являются Chef Workstation, которая является автономной рабочей станцией оператора, Chef Infra Client (агент хоста), который работает на хостах и извлекает шаблоны конфигурации и вносит необходимые изменения, и Chef Infra Server, который отвечает на запросы от Chef Infra Agents на проверяет хосты и отвечает обновлениями конфигурации, после чего агенты объединяют конфигурацию хоста.

### Инфраструктура как код

Неизменяемость буквально означает «состояние неизменности», но на языке DevOps это относится к поддержке систем полностью как коду, без выполнения каких-либо ручных операций над ними. Приверженность неизменности позволяет вам обращаться с базой кода автоматизации, как с любым кодом приложения:

* Вы можете быть уверены, что кодовая база описывает, что на самом деле работает на голом железе или на облачных серверах.
* Вы можете управлять процедурами Agile базы кода и структурированным использованием контроля версий, чтобы все было ясно и просто.

### Автоматизация тестирования

DevOps обычно требует более детальных способов определения и реализации инфраструктур, удостоверения того, что развернутые инфраструктуры работают должным образом, проактивного обеспечения бесперебойной работы, упреждающего принятия мер при неизбежных сбоях, а также поиска и устранения проблем при возникновении ошибок.

Когда вы используете инструменты модульного тестирования, такие как pytest, в тандеме с автоматизацией более высокого порядка и в сочетании с непрерывной доставкой (CI/CD), вы можете создавать среды, в которых код может быть автоматически протестирован при внесении изменений.

Фреймворки модульного тестирования делают тесты частью вашей кодовой базы, следуя коду через коммиты разработчика, запросы на вытягивание и выходы для проверки кода в QA/test и Production. Это особенно полезно в средах разработки, управляемой тестированием (TDD), где написание тестов - это непрерывный процесс, который фактически ведет разработку, автоматически обеспечивая очень высокий уровень покрытия тестами.

### Сетевое моделирование

Сетевое моделирование предоставляет средства для тестирования сетевых конфигураций, отладки кода конфигурации, а также для работы и изучения инфраструктуры Cisco и API-интерфейсов безопасным, удобным и недорогим способом.

Cisco Virtual Internet Routing Laboratory (VIRL) VIRL может работать на «голом железе» или на больших виртуальных машинах на нескольких гипервизорных платформах.

<!-- 7.8.2 -->
<!-- quiz -->