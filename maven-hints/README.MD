# Commands

$ mvn help:effective-pom  - смерженный пом всех помов(карента, родительского и супер)

$ mvn dependency:tree  --list of all dependencies into your project 

$ mvn clean install -DproxySet=true -DproxyHost=ur.proxy.server -DproxyPort=port   --PROXY IN COMMAND LINE


# VERSION DEPENDENCY REGEXP RULES
equal rule-----------------------------------------------------------------------

1.2	             ||   Version equals to 1.2 or is starting with 1.2
[1.2]	         ||   Only version 1.2 only.x == 1.0
less rule------------------------------------------------------------------------
(,1.2]           ||   Any version less than 1.2. Version 1.2 included. x <= 1.2
(,1.2)	         ||   Any version less than 1.2. Version 1.2 excluded. x < 1.2
greater rule---------------------------------------------------------------------
[1.2,)	         ||   Any version greater than 1.2. Version 1.2 included. x >= 1.2
(1.2,)	         ||   Any version greater than 1.2. Version 1.2 excluded. x > 1.2
between rule---------------------------------------------------------------------
(1.2,2.2)        ||	Version between 1.2 and 2.2. Both excluded. 1.0 < x < 2.0
[1.2,2.2]        ||	Version between 1.2 and 2.2. Both included. 1.2 <= x <= 2.2
(,1.2],[2.2,)    ||   x <= 1.2 or x >= 2.2

# GET PROPERTY
${project.build.directory} - "target" директория, или тоже самое ${pom.project.build.directory}.
${project.build.outputDirectory} - путь к директории куда компилятор складывает файлы по умолчанию "target/classes".
${project.name} или ${pom.name} - имя проекта.
${project.version} или ${pom.version} - версия проекта.

# DEPENDENCY SCOPES - видимость зависимостей
compile, provided, runtime, test, system, and import

<scope>compile</scope>      || Область видимости по умолчанию. Зависимости с этим scope будут доступны и во время сборки и во время 
                               тестирования и их даже добавят в конечный пакет, чтобы они были доступны и во время исполнения. 
                               Более того, maven распространит их дальше и сделает доступными в зависимых пакетах
<scope>provided</scope>     || Почти как compile, но в пакет зависимость добавлена не будет. Предполагается что данные библиотеки будут
                               предоставлены средой выполнения, например OpenShift контейнером. Каноничный пример такой зависимости — OpenShift API,
                               конкретная реализация которых предоставляется контейнером OpenShift
<scope>runtime</scope>      || антипод provided. Означает зависимость, которая требуется для исполнения/тестирования кода, но не для его сборки.
                               Зависимости из этого scope так же будут добавлены в пакет.
<scope>test</scope>         || Зависимости, которые нужны только и исключительно для тестов. Как JUnit из примера выше.   
<scope>system</scope>       || зависимость которая присутствует в среде Java всегда, тем или иным путём. Maven не будет пытаться предоставить этот артефакт или класть
                               его в пакет итд       
<scope>iport</scope>       || использутся для импорта зависимостей из других артефактов и управлением зависимостями в сложных пакетах, состоящих из нескольких артефактов                                                             
   
Examples: provided - Lombok, JUnit - test, log4j - runtime