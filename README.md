# DBManager
Datebases manager for our beloved "1 ass"

# Внешний вид
![alt text](https://github.com/seriouskeks/DBManager/blob/master/Images/Skins.jpg)

# Описание
При первом запуске будет произведен поиск каталогов шаблонов, кэша, релизов платформы. Так же будет установлен путь к файлу с базами (*ibases.v8i*) по умолчанию в каталог программы. При необходимости возможен импорт существующих баз. Для этого необходимо выбрать соответствующий файл в настройках (каталог по умолчанию, с которым работает 1С: *"%AppData%\1C\1CEStart"*), с созданием бэкапа (при изменении пути будет выдан запрос на сохранение).
После запуска необходимо проверить автоматически подобранные пути и при необходимости изменить. 
Рабочее поле программы делится на 2 половины. Слева расположены группы: 3 группы по умолчанию + группы вводимые пользователем. Справа - непосредственно список баз данных. Добавление групп и баз осуществляется по клику кнопки "+" в конце каждого из списков. Изменение порядка пользовательских групп и баз, а так же перемещение баз в группы осуществляется с помощью перетаскивания.

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

__Действия с базами данных (кнопка "Дополнительно" на топ уровне, применяется ко всем базам):__
* Поиск/Удаление неиспользуемых баз (см. соответствующий раздел)
* Отключение автоматической авторизации
* Запуск конфигуратора по двойному клику 

# Поиск/Удаление неиспользуемых баз
По кнопке "Выбрать директорию сканирования" осуществляется выбор директории, в которой будет произведен поиск файловых баз (`*`.1CD), которых нет в списке баз выбранного файла *ibases.v8i*.
Базы к удалению отмечаются галками и жмется кнопка "Обработать". 
ВНИМАНИЕ ! Директории баз данных будут удалены безвозвратно.

![alt text](https://github.com/seriouskeks/DBManager/blob/master/Images/FindRedundantDB.jpg)

# Подключаемые дополнение
Для добавления аддонов в меню "Дополнения" необходимо создать ini файл с именем, которым аддон будет доступен в меню и поместить в директорию "Addons".
В ini возможно указание любых параметров строки соединения (см.справку 1С), учитывая особенности параметров (например выполнение внешней обработки может быть доступно только при выборе определенного релиза платформы).
ini файл должен содержать в себе только 1 строку.
Возможно указание текущей папки аддонов параметром *%ТекущаяДиректория%*.
Пример реализации можно посмотреть на аддонах по блокировке сеансов для конфигураций на основе БСП.

