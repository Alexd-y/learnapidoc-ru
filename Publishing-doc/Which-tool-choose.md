# Рекомендации выбора инструментов документирования

В разделах [Генераторы статичных сайтов](Static-site-generators.md), [Варианты хостинга и развертывания](Hosting-and-deployment-options.md) и [Возможности автономных CMS (и Readme.io)](Headless-cms-options.md) описана совокупность инструментов для ведения документации. Какое решение выбрать? Это сложное решение, которое будет требовать компромиссов. Решение зависит от навыков технического писателя, продукта, среды и требований. Но вот общая рекомендация:

- определить, какие есть требования к созданию документации;
- выбрать генератор статичных сайтов;
- выбрать платформу хостинга и развертывания.

[Определяем требования](#define)

[1. Выбираем генератор статичных сайтов](#generator)

[2. Выбираем платформу хостинга и деплоя](#hosting)

[3. Определяем, как парсить спецификацию OpenAPI](#parsing)

[Инструменты против контента](#versus)

<a name="define"></a>
## Определяем требования

Первым шагом к выбору инструмента является определение требований к разработке. Начинаем с ответов на следующие вопросы:

- Будут ли разработчики активно работать над контентом?
- Существуют ли ограничения безопасности по использованию сторонних платформ для размещения документации, таких как GitHub?
- Существует ли  внутренняя инфраструктура, которую надо подключить для хранения и автоматического создания сайта?
- Существуют ли инженерные ресурсы для реализации собственного процесса публикации с непрерывной доставкой?
- Насколько хорошо знаком конкретный язык программирования?
- Сколько примерно страниц документации планируется для проекта?
- Есть ли навыки веб-разработки (или доступ к UX-ресурсам) для разработки или модификации тем сайта?
- Будет ли выделен бюджет для оплаты стороннего хостинга и варианта развертывания?
- Сколько писателей будут непосредственно участвовать в проекте?
- Нужна ли аутентификация документации для конкретных пользователей? Существует ли система аутентификации компании?
-  Нужна ли интеграция документации непосредственно в сайт компании, с тем же брендом и внешним видом?
- Нужна ли локализация контента? Если да, то на сколько  языков? Существуют ли требования к форматированию, предъявляемые поставщиком переводов и системой?
- Нужно ли создавать PDF-материалы для контента (в дополнение к веб-выводу)?
- Нужно ли много контроля и гибкости, для расширения или настроек решение в соответствии с потребностями конкретного документа, что может включать в себя длительные пользовательские сценарии или интеграцию с другой системой?
- Можно ли использовать внешнюю службу поиска, такую ​​как Swiftype, Algolia или Google Custom Search?
- В какой степени нужно повторное использование одного и того же контента в нескольких экземплярах или выходных данных?
- Нужно ли версионирование документации с каждым новым релизом?

После сбора требований придется принять, что единая система, отвечающая всем требованиям не существует. Есть компромиссы для выбора каждого инструмента. Вопрос в том, какие функции приоритетнее.

Например, может быть важно сократить время, затрачиваемое на инструменты, чем иметь собственный бренд и отображение. Или, возможно, современный веб-вывод важнее, чем возможность создавать PDF-файлы. Или, возможно, должна быть аутентификация документации, но  нет бюджета. Придется принимать трудные решения.

<a name="generator"></a>
## 1. Выбираем генератор статичных сайтов

Если нужна мощность и контроль для создания нужных сложных функций (создание собственной темы или сайта документации с уникальным брендированием) нужно использовать генератор статичных сайтов, такой как [Hugo](Static-site-generators.md#hugo), [Sphinx](Static-site-generators.md#sphinx) или [Jekyll](Static-site-generators.md#jekyll). Если есть серьезные потребности в документации (после перехода из мира DITA с привычкой работать с более надежным инструментам), понадобится платформа, удовлетворяющая такие потребности. Jekyll, Sphinx и Hugo предлагают такие возможности в своих платформах.

Конечно, мощность и контроль потребуют обучения, но можно начать работать с готовой темой, а затем, по желанию, кастомизировать все под себя.

Если нет навыков веб-разработки и нет желания возиться с темами или другой разработкой кода, можно выбрать решение, такое как [Readme.io](Headless-cms-options.md#readmeio) или [Netlify CMS](Headless-cms-options.md#netlify) (хотя в Netlify CMS все равно придется выбирать темы). Readme предоставляет готовый дизайн для сайта документации API, устраняя необходимость в разработке темы и определении хостинга / развертывания? что может сэкономить много времени и усилий.

Нужно осознать, что при реализации решения можно потратить четверть своего времени (в течение нескольких месяцев между проектами), настраивая тему и работая над инструментами для работы с документацией. Если нет желания уделять столько времени своим инструментам, Readme - хороший вариант. Возможно, кто-нибудь захочет больше контроля и гибкости над информационным дизайном и темой оформления. Кому-то нравится экспериментировать, и есть желание кодировать любые нужные функции, такие как [встроенная навигационная карта](https://idratherbewriting.com/simplifying-complexity/macro-micro.html), [функции JS для свертывания / развертывания элементов](https://idratherbewriting.com/simplifying-complexity/hiding-complexity.html), [кастомные метаданные](https://idratherbewriting.com/simplifying-complexity/discoverability-through-metadata.html) или что угодно. Многие технические писатели и разработчики хотят подобные возможности. Что важно? Гибкость и контроль настолько важны, что можно потратить недели / месяцы времени на настройку инструмента?

Кроме того, если есть большое количество писателей, которым потребуется прямой доступ к системе, подумайте, есть ли бюджет для решения, такого как Readme, которое берет плату за каждого писателя.

Если есть желание использовать генератор статичных сайтов, какой из них выбрать - Jekyll, Hugo, Sphinx или какой-то другой? Sphinx имеет наиболее ориентированные на документацию функции, такие как поиск, PDF, перекрестные ссылки и семантическая разметка. Если эти функции важны, надо выбирать Сфинкс.

Выбор Jekyll или Hugo вместо Sphinx имеет смысл, поскольку их сообщества выходят за пределы групп документации. Sphinx был разработан как платформа для документации, поэтому его аудитория имеет тенденцию быть более нишевой. Инструменты документации почти никогда не имеют такого размера сообщества, как более общие инструменты веб-разработки. Таким образом, компромисс для Jekyll или Hugo заключается в том, что, хотя им не хватает некоторых более качественных возможностей (перекрестные ссылки, поиск, PDF, семантическая разметка), они имеют большие сообщества и импульс в долгосрочной перспективе. Тем не менее, может поставить в затруднительное положение, если нужно будет найти решение для поиска, PDF и перевода (которые выполнимы, но не из коробки).

Разметка также может стать камнем преткновения. Если выбор пал на Sphinx с reStructuredText или Jekyll / Hugo с Markdown, то один вопрос, который нужно задать, заключается в том, будут ли разработчики в компании писать в reStructuredText (если они вообще будут писать). Если они напишут в reStructuredText, отлично, Sphinx, вероятно, лучше для проектов документации из-за [семантических преимуществ reStructuredText](More-about-Markdown.md#semantic). Но если разработчики настаивают на Markdown, то, возможно, Jekyll или Hugo будут лучшим выбором.

Следует учитывать, что гибкость есть даже в выбранном  генераторе статичных  сайтов. Например, можно использовать Markdown совместно с Sphinx, но при этом некоторые функции Sphinx становятся ограниченными. Также можно использовать Asciidoc с Jekyll через [плагин jekyll-asciidoc](https://github.com/asciidoctor/jekyll-asciidoc).

При выборе между Jekyll и Hugo, стоит учитывать размер проекта. Тысячи страниц в одном проекте? Каждый писатель строить проект локально? Если да, то насколько важна скорость (насколько быстро проект компилирует выходные данные)? Если скорость является важным фактором, Hugo -  лучший выбор. Но если нужны сообщество и платформа, которая тесно интегрируется с GitHub, то лучше выбрать Jekyll. Написание собственных сценариев Liquid в Jekyll также проще, чем в Go в Hugo.

<a name="hosting"></a>
## 2. Выбираем платформу хостинга и деплоя

После выбора генератора статичного сайта переходим к выбору вариантов размещения и развертывания (с опцией CD). Если в качестве генератора статичных сайтов был выбран Sphinx, то для хостинга лучше выбрать [Read the Docs](Hosting-and-deployment-options.md#readthedocs). Для Jekyll, подойдут [GitHub Pages](Hosting-and-deployment-options.md#githubPages), [CloudCannon](Hosting-and-deployment-options.md#cloudCannon), [Netlify](Hosting-and-deployment-options.md#netlify) или [Aerobatic](Hosting-and-deployment-options.md#aerobatic). Для Hugo, возьмем [Netlify](Hosting-and-deployment-options.md#netlify) или [Aerobatic](Hosting-and-deployment-options.md#aerobatic). Используя одну из этих платформ, технический писатель снимает с себя огромную нагрузку на обслуживание сервера и развертывание своего сайта.

Обычно внутри компании группы разработки управляют и контролируют серверную инфраструктуру. Настройка и поддержка собственного сервера для документации с использованием только внутренних ресурсов может быть значительным расходом и головной болью. Инжиниринг может занять месяцы (если не годы), чтобы освободить место на сервере, и даже если это осуществится, вряд ли там будет и половина необходимых функций (таких как CD и CLI). Вот почему сторонние хостинг и варианты развертывания лучше.

Обслуживание собственного сервера - это не то дело, чем следует заниматься, а сторонние платформы позволяют быть более эффективным. Устранение проблем с публикацией посредством непрерывной доставки с сервера упрощает жизнь писателя. С другой стороны, если есть группа поддержки инструментов разработки и у них есть пропускная способность и интерес к поддержке технических документов, использование внутренних инструментов может облегчить интеграцию с другими инструментами (такими как проверочное тестирование), доступными в компании.

Если компания предпочитает создавать собственный конвейер публикаций, прежде чем идти по этому пути, нужно выяснить, какие функции предоставит внутреннее решение. Стоит изучить преимущества сторонних хостов и вариантов развертывания и выяснить, будет ли у внутреннего решения нужные возможности. При наличии сильной технической поддержки все отлично. Но если разработчики едва дадут на раздумья очень короткий срок, лучше смотреть в сторону стороннего решения. Нечто подобное описано в разделе [Пример из практики: переключение инструментов в docs-as-code](Switching-tools.md).

Если нет бюджета на сторонний хост и опцию развертывания, а также нет внутренних ресурсов, можно рассмотреть возможность развертывания [AWS S3 buket](https://aws.amazon.com/ru/s3/). У Jekyll есть плагин под названием [S3_website](https://github.com/laurilehmijoki/s3_website), который легко развертывается на S3. Это не модель непрерывной доставки, но она также не включает загрузку всей информации сайта при каждой публикации. Плагин S3_website смотрит на то, что изменилось в выходных данных, и синхронизирует эти изменения с файлами на S3.

Даже не используя Jekyll, можно использовать GitHub Pages в качестве бесплатного хоста публикации для любого вывода генератора статичных сайтов. Файлы просто создаются локально, а затем помещаются в репозиторий с поддержкой GitHub-Pages. При таком подходе сервер не будет выполнять процесс сборки, но будет обработка процесса через командную строку. Бесплатный хостинг для документации на GitHub, независимо от инструмента, может быть и удобным.

<a name="parsing"></a>
## 3. Определяем, как парсить спецификацию OpenAPI

[Спецификация OpenAPI](../openAPI-specification/introduction-openapi-and-swagger.md) также может быть важным фактором при рассмотрении инструментов. Как предстоит отображать [справочную документацию по конечной точке](../documenting-api-endpoints/README.md)? Вместо того, чтобы [создавать собственный шаблон](Design-patterns.md) или определять справочные разделы вручную, лучше использовать инструмент, который может считывать и анализировать OpenAPI для справочной документации. Не многие автономные инструментальные средства для документации [легко включают и отображают спецификацию OpenAPI](../openAPI-specification/integrating-swagger-with-docs.md) (пока), поэтому, возможно, лучшей альтернативой может быть либо ссылка на [Swagger UI](../openAPI-specification/swagger-ui-tutorial.md) или встраивание в нее документации (при отсутствии ресурсов UX для более глубокой интеграции).

Генераторы статичных сайтов могут преобразовать любой веб-сайт HTML в тему, содержание которой обеспечивается генератором статичных сайтов - статья [Convert an HTML site to Jekyll](https://jekyllrb.com/tutorials/convert-site-to-jekyll/) (учебник, написанный автором курса).

<a name="versus"></a>
## Инструменты против контента

Хотя в этом разделе основное внимание уделяется инструментам, стоит подчеркнуть, что контент всегда выше инструментов. Контент должен быть основным фокусом, а не инструменты, которые используются для публикации контента. После создания инфраструктуры инструментов, она (инфраструктура) в основном должна отойти на задний план в повседневных задачах разработки контента.

> Отличная статья о важности контента над инструментами приведена в разделе[ Good API Documentation Is Not About Choosing the Right Tool](https://blog.algolia.com/api-documentation-choosing-right-tool/) в блоге Algolia. Автор объясняет, что «качественный файл README.md, хранящийся на GitHub, может быть гораздо более эффективным, чем чрезмерно спроектированная документация, которая хорошо отображается, но имеет проблемы с контентом».

В некотором смысле, инструменты - это как обувь баскетболиста. Конечно, хорошая обувь имеет значение. Но Майкл Джордан не был великим баскетболистом, потому что он носил Nikes, и Коби Брайант не был великим из-за его Adidas. Можно написать невероятную документацию и без инструментов и платформы. Не нужно позволять инструментам отвлекать внимание от того, что действительно важно в роли технического писателя: содержания.

Можно неоднократно менять платформы документации, и редко кто-то даже заметит это. Пока это выглядит прилично, большинство руководителей проектов и пользователей будут ориентироваться на контент гораздо больше, чем на дизайн или платформу. В некотором смысле дизайн должен быть невидимым и ненавязчивым, не фокусируясь на содержании. Пользователь не должен отвлекаться на инструменты.

Кроме того, пользователи и рецензенты не заметят (или не оценят) все усилия, прилагаемые к инструментам. Даже когда удается создать единый исходный контент, просмотреть собственную коллекцию, чтобы создать специальный дисплей, включить переключатели языка для перехода с платформы на платформу и т.д., можно получить ответ: «Здесь опечатка». Или «Какой тип данных для этого параметра?»

С другой стороны, выбранные инструменты, имеют огромное значение для производительности, возможностей и общего счастья технического писателя. Выбор неправильного инструмента может лишить возможности предоставлять документацию, которая нужна пользователям.
