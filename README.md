# DBManager
Datebases manager for our beloved "1 ass"

# Требования
Минимальный релиз платформы 1С 8.3.*. Для запуска программы необходимо установить виртуальную машину [JAVA (JRE)](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) не ниже версии 1.8. Так же использование программы подразумевает соглашение с лицензией [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0)

# Внешний вид
![alt text](https://github.com/seriouskeks/DBManager/blob/master/Images/Skins.jpg)

# Описание
При первом запуске будет произведен поиск каталогов шаблонов, кэша, релизов платформы. Так же будет установлен путь к файлу с базами (*ibases.v8i*) по умолчанию в каталог программы. После загрузки рекомендуется выполнить импорт существующих баз (иначе не будет возможности использовать функционал работы с кэшем для баз созданных через данную программу). Для этого необходимо выбрать соответствующий файл в настройках (каталог по умолчанию, с которым работает 1С: *"%AppData%\1C\1CEStart"*), с созданием бэкапа (при изменении пути будет выдан запрос на сохранение).

*После запуска необходимо проверить автоматически подобранные пути и при необходимости изменить.*

Рабочее поле программы делится на 2 половины. Слева расположены группы: 3 группы по умолчанию + группы вводимые пользователем. Справа - непосредственно список баз данных. Добавление групп и баз осуществляется по клику кнопки ➕ в конце каждого из списков. Изменение порядка пользовательских групп и баз, а так же перемещение баз в группы осуществляется с помощью перетаскивания.

__Действия с базами данных (отдельно для каждой базы):__
* Запуск в режиме предприятия (управляемое, обычное приложение, запуск с указанием кода блокировки)
* Запуск в режиме конфигуратра 
* Запуск в режиме тестирования (менеджер тестирования, клиент тестирования, запуск с записью интерактивных действий пользователя)
* Возможность удаления базы с диска паралелльно с удалением из списка
* Определение релиза, под которым будет осуществляться работа с базой 
* Указание пользователя, который будет использоваться для автоматической авторизации при запуске (рекомендуется к использованию, но только при уверенности, что файл настроек не попадет в чужие руки)
* Блокирование регламентных заданий (для файловых баз)
* Использовать сжатие (для клиент-серверных баз)
* Не выводить предупреждения при старте ("конфигурация была изменена" и т.д.)
* Загрузка/Выгрузка конфигурации и базы данных без необходимости заходить в конфигуратор
* Обновление/Динамическое обновление без необходимости заходить в конфигуратор 
* Откат конфигурации до конфигурации ИБ
* Восстановление структуры ИБ при ошибках
* Открытие директории/Удаление пользовательского кэша и кэша конфигурации
* Подключаемые дополнение (см. соответствующий раздел). Для примера реализованы аддоны по установке/снятию блокировки сеансов.
* Возможность создавать базу с предзагруженными `*.cf`, `*.dt` 
* Возможность указания размера страницы базы данных в файловом варианте, позволяя использовать файловую базу, а не клиент-серверный вариант для больших баз  

__Действия с базами данных (кнопка "Дополнительно" на топ уровне, применяется ко всем базам):__
* Поиск/Удаление неиспользуемых баз (см. соответствующий раздел)
* Отключение автоматической авторизации
* Запуск конфигуратора по двойному клику 

# Поиск/Удаление неиспользуемых баз
По кнопке "Выбрать директорию сканирования" осуществляется выбор директории, в которой будет произведен поиск файловых баз (`*.1CD`), которых нет в списке баз выбранного файла *ibases.v8i*.
Базы к удалению отмечаются галками и жмется кнопка "Обработать". 

__ВНИМАНИЕ ! Выбранные директории баз данных будут удалены безвозвратно. Внимательно проверьте путь к удаляемой директории, например чтобы в удаляемой директории не было вложенных "рабочих баз" или удаляемая база не располагалась в корне системного диска, например "C:\", иначе возможен "неприятный сюрприз".__ 

![alt text](https://github.com/seriouskeks/DBManager/blob/master/Images/FindRedundantDB.jpg)

# Подключаемые дополнения
Для добавления аддонов в меню "Дополнения" необходимо создать ini файл с именем, которым аддон будет доступен в меню и поместить в директорию "Addons".
В ini возможно указание любых параметров строки соединения (см.справку 1С).
ini файл должен содержать в себе только 1 строку.
Возможно указание текущей папки аддонов параметром *%ТекущаяДиректория%*.
Пример реализации можно посмотреть на аддонах по блокировке сеансов для конфигураций на основе БСП.

# Обновления

v.1.0.2 - Добавлена возможность указания релиза по умолчанию для работы с базой (раздел "Меню"). Если автоматом путь подбирается к релизу ниже 8.3, то необходимо выбрать либо определенный релиз платформы 8.3 (файл '1cv8.exe'), либо файл '1cestart.exe', чтобы выбирался всегда последний релиз.

v.1.0.3 - Добавлено визуальное выделение файловых баз в списке с отсутствующими файлами на диске.

