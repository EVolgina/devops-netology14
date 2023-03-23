# 1. Проверьте список доступных сетевых интерфейсов на вашем компьютере. Какие команды есть для этого в Linux и в Windows?
ответ: Все файлы устройств сетевых интерфейсов находятся в папке /sys/class/net. Поэтому вы можете посмотреть её содержимое:
ls /sys/class/net . В файле /proc/net/dev тоже содержится список всех сетевых интерфейсов, а также статистика их использования:
cat /proc/net/dev
![]()
Утилита ifconfig выводит не только список сетевых интерфейсов, но и информацию о них, такую как состояние, IP адрес, MAC адрес и другие параметры. Для отображения всех интерфейсов достаточно выполнить программу без параметров:
ifconfig
![]()
ip link show - объединяет в себе функции нескольких программ, например ifconfig, route, brctl и других
ip -br link show
![]()
Посмотреть всю нужную информацию можно и с помощью консольной утилиты управлением брандмауэром - nmcli: $ nmcli device status\
Программа netstat тоже умеет показывать сетевые интерфейсы и статистику по переданным данным если ей передать опцию -i:$ netstat -i
Для Windows 10
IPConfig является одним из наиболее распространённых сетевых инструментов, позволяющим запрашивать и отображать текущую конфигурацию сети TCP/IP (протокол управления передачей/интернет-протокол). Команда также содержит параметры для выполнения различных действий, таких как обновление параметров протокола динамической конфигурации хоста (DHCP) и системы доменных имен (DNS)
![ipconfig](https://github.com/EVolgina/devops-netology14/blob/main/ipconfig.JPG)
 чтобы просмотреть всю конфигурацию сети TCP/IP, и нажмите ввод: ipconfig /all\
 ![ipc](https://github.com/EVolgina/devops-netology14/blob/main/ipconfigall.JPG)
 Ping является ещё одним важным сетевым инструментом. Он позволяет отправлять сообщения эхо-запроса ICMP (Internet Control Message Protocol)\
 для проверки IP-соединения с другими устройствами, будь то другой компьютер в локальной сети или интернет-сервис\
 ![ping](https://github.com/EVolgina/devops-netology14/blob/main/ping.JPG)
 Tracert-Trace Route -диагностический инструмент для определения сетевого пути к месту назначения с помощью серии эхо-запросов ICMP. Однако,\
 в отличие от команды ping, каждый запрос включает значение TTL (время жизни), которое увеличивается на единицу каждый раз, что позволяет\
 отображать список пройденного маршрута и продолжительность\
 ![tracert](https://github.com/EVolgina/devops-netology14/blob/main/tracer%20g.JPG)
 Инструмент netstat (Сетевая статистика) отображает статистику всех сетевых подключений. Это позволяет видеть открытые и подключенные порты, чтобы отслеживать и устранять сетевые проблемы для Windows 10 и приложений.
 ![netstat](https://github.com/EVolgina/devops-netology14/blob/main/netstst.JPG)
 ARP-Windows 10 поддерживает таблицу arp (протокол разрешения адресов), в которой хранятся записи IP в Media Access Control (MAC), разрешённые\
 системой. Инструмент arp позволяет просматривать всю таблицу, изменять записи и использовать её для определения MAC-адреса удалённого компьютера\
 ![arp](https://github.com/EVolgina/devops-netology14/blob/main/arp.JPG)
  Route-инструмент маршрутизации отображает таблицу маршрутизации, которая позволяет Windows 10 понимать сеть и взаимодействовать с другими\
  устройствами и службами. Инструмент также предлагает некоторые параметры для изменения и очистки таблицы при необходимости.\
  ![route](https://github.com/EVolgina/devops-netology14/blob/main/route.JPG)
  

Как и в случае с инструментом arp, обычно не нужно беспокоиться о таблице маршрутизации. И всё же, этот инструмент командной строки пригодится при устранении проблем.

# 2. Какой протокол используется для распознавания соседа по сетевому интерфейсу? Какой пакет и команды есть в Linux для этого?
Используется пакет sudo apt-get install lldpd, команда lldpctl. Протокол – LLDP (протокол для обмена информацией меж-ду соседними устройствами, позволяет определить к какому порту коммутатора подключен сервер).

# 3. Какая технология используется для разделения L2-коммутатора на несколько виртуальных сетей? Какой пакет и команды есть в Linux для этого? Приведите пример конфига.
Технология называется VLAN (Virtual LAN).
Пакет в Ubuntu Linux - vlan
Пример конфига:
# 4. Какие типы агрегации интерфейсов есть в Linux? Какие опции есть для балансировки нагрузки? Приведите пример конфига.

# 5. Сколько IP-адресов в сети с маской /29 ? Сколько /29 подсетей можно получить из сети с маской /24. Приведите несколько примеров /29 подсетей внутри сети 10.10.10.0/24.

# 6. Задача: вас попросили организовать стык между двумя организациями. Диапазоны 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 уже заняты. Из какой подсети допустимо взять частные IP-адреса? Маску выберите из расчёта — максимум 40–50 хостов внутри подсети.

# 7.Как проверить ARP-таблицу в Linux, Windows? Как очистить ARP-кеш полностью? Как из ARP-таблицы удалить только один нужный IP?
