<!-- 4.5.1 -->
## Аутентификация REST API

Merriam-Webster определяет аутентификацию как «… действие, процесс или метод демонстрации чего-либо (например, личности) как реального, истинного или подлинного». По соображениям безопасности большинство REST API требует аутентификации, чтобы случайные пользователи не могли создавать, обновлять или удалять информацию неправильно или злонамеренно, а также получать доступ к информации, которая не должна быть общедоступной. Без аутентификации REST API позволяет любому получить доступ к функциям и системным службам, которые были представлены через интерфейс. Требование аутентификации - это то же самое, что требование учетных данных имени пользователя и пароля для доступа к странице администрирования приложения.

Некоторые API не требуют аутентификации. Эти API-интерфейсы обычно доступны только для чтения и не содержат критической или конфиденциальной информации.

<!-- 4.5.2 -->
## Аутентификация и авторизация

При работе с REST API важно понимать разницу между аутентификацией и авторизацией, поскольку эти два термина часто используются как взаимозаменяемые или неправильно. Знание разницы поможет вам устранить любые проблемы, связанные с безопасностью вашего запроса REST API.

### Аутентификация

![](./assets/4.5.2-1.png)
<!-- https://contenthub.netacad.com/courses/devnet/337c1050-b012-11ea-8a1b-c929643d7563/33931ac0-b012-11ea-8a1b-c929643d7563/assets/9780d9b2-bcc3-11ea-af32-dfde9d560aae.svg -->

Аутентификация подтверждает личность пользователя

Аутентификация - это акт проверки личности пользователя. Пользователь доказывает, что они такие, о которых говорят. Например, когда вы едете в аэропорт, вам необходимо предъявить удостоверение личности государственного образца или использовать биометрические данные, чтобы доказать, что вы являетесь тем человеком, которым вы себя называете.

### Авторизация

![](./assets/4.5.2-2.png)
<!-- /courses/devnet/337c1050-b012-11ea-8a1b-c929643d7563/33931ac0-b012-11ea-8a1b-c929643d7563/assets/9780d9b3-bcc3-11ea-af32-dfde9d560aae.svg -->

Авторизация определяет доступ пользователя

Авторизация - это подтверждение пользователем того, что у него есть разрешения на выполнение запрошенного действия с этим ресурсом. Например, когда вы идете на концерт, все, что вам нужно предъявить, - это билет, чтобы доказать, что вы можете войти. Вам не обязательно удостоверять свою личность.

<!-- 4.5.3 -->
## Механизмы аутентификации

Общие типы механизмов аутентификации включают в себя базовый, носитель и API-ключ.

### Базовая аутентификация

Обычная проверка подлинности, также известная как базовая аутентификация, использует стандартную схему проверки подлинности Basic HTTP. Базовая аутентификация передает учетные данные в виде пар имени пользователя и пароля, разделенных двоеточием (`:`) и закодирован с использованием Base64.

В запросе REST API информация Basic Auth будет предоставлена в заголовке:

```
Authorization: Basic <username>:<password>
```

Обычная аутентификация - это простейший механизм аутентификации. Это крайне небезопасно, если оно не связано с запросами, использующими HTTPS, а не HTTP. Хотя учетные данные закодированы, они не зашифрованы. Расшифровать учетные данные и получить пару имени пользователя и пароля просто.

### Аутентификация на предъявителя

Аутентификация на предъявителя, также известная как аутентификация токена, использует стандартную схему проверки подлинности HTTP на носителе. Он более безопасен, чем обычная проверка подлинности, и обычно используется с OAuth (обсуждается позже) и с единым входом (SSO). Аутентификация на предъявителя использует токен на предъявителя, который представляет собой строку, сгенерированную сервером аутентификации, например, службой идентификации (IdS).

В запросе REST API информация об аутентификации носителя будет предоставлена в заголовке:

```
Authorization: Bearer <bearer token>
```

Как и обычная проверка подлинности, проверку подлинности на предъявителя следует использовать с HTTPS.

### Ключ API

Ключ API, также называемый токеном API, представляет собой уникальную буквенно-цифровую строку, генерируемую сервером и назначаемую пользователю. Чтобы получить уникальный ключ API, пользователь обычно входит в портал, используя свои учетные данные. Этот ключ обычно назначается один раз и не восстанавливается. Все запросы REST API для этого пользователя должны предоставлять назначенный ключ API в качестве формы аутентификации.

Как и в случае с другими типами аутентификации, ключи API безопасны только при использовании с HTTPS.

Ключи API предназначены для использования в качестве механизма аутентификации, но обычно неправильно используются в качестве механизма авторизации.

Есть два типа ключей API: открытые и частные.

Открытый ключ API может быть общим и позволяет этому пользователю получить доступ к подмножеству данных и API. Не сообщайте закрытый ключ, потому что он похож на ваше имя пользователя и пароль. Срок действия большинства ключей API не истекает, и если ключ не может быть отозван или восстановлен, если он будет распространен или скомпрометирован, любой, у кого есть этот ключ, может неограниченно долго обращаться к системе, как и вы.

Запрос REST API может предоставить ключ API несколькими способами:

* Строка запроса: рекомендуется только для открытых ключей API
* Заголовок: использует ключ авторизации или настраиваемый ключ `Authorization: <API Key>` или `Authorization: APIkey <API Key>` или `APIkey: <API Key>`
* Основные данные: в качестве идентификатора используется уникальный ключ `Content-Type: application/json`
* Cookie: в качестве идентификатора используется уникальный ключ `Cookie: API_KEY=<API Key>`

<!-- 4.5.4 -->
## Механизмы авторизации

### Механизмы авторизации

Открытая авторизация, также известная как OAuth, сочетает аутентификацию с авторизацией. OAuth был разработан как решение проблемы небезопасных механизмов аутентификации. Благодаря повышенной безопасности по сравнению с другими вариантами, это обычно рекомендуемая форма аутентификации/авторизации для REST API.

Существует две версии OAuth, называемые просто OAuth 1.0 и OAuth 2.0. Большинство современных REST API реализуют OAuth 2.0. Обратите внимание, что OAuth 2.0 не имеет обратной совместимости.

Согласно определению в структуре авторизации OAuth 2.0, «структура авторизации OAuth 2.0 позволяет стороннему приложению получать ограниченный доступ к службе HTTP, либо от имени владельца ресурса, организуя согласование взаимодействия между владельцем ресурса и службой HTTP, либо разрешив стороннему приложению получить доступ от своего имени».

По сути, OAuth 2.0 позволяет предварительно зарегистрированным приложениям получать авторизацию для выполнения запросов REST API от имени пользователя, при этом пользователю не нужно делиться своими учетными данными с самим приложением. OAuth позволяет пользователю предоставлять учетные данные непосредственно серверу авторизации, обычно провайдеру удостоверений (IdP) или службе удостоверений (IdS), для получения токена доступа, который можно использовать совместно с приложением.

Этот процесс получения токена называется потоком. Затем приложение использует этот токен в REST API в качестве аутентификации на предъявителя. Затем веб-служба для REST API проверяет сервер авторизации, чтобы убедиться, что токен действителен, и что запрашивающая сторона имеет право выполнять запрос.
