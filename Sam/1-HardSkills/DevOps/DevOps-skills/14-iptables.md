**iptables** - выполняет функцию межсетевого экрана
	
![[Pasted image 20220829083318.png]]

Список основных команд и опций:
1. Действия
-A: Добавление правила в конец списка (iptables -A INPUT -s 192.168.0.15 -j DROP – запретить входящие с 192.168.0.15)
-D: Удаление правила (iptables -D INPUT 10 удалить правило в цепочке INPUT с номером 10)
-I: Вставка правила в определенную часть списка (iptables -I INPUT 5 -s 192.168.0.15 -j DROP вставить правило 5-м по списку)
-R: Замена правила iptables (-R OUTPUT 5 -s 192.168.0.15 -j ACCEPT заменить 5-е правило с запрещающего на разрешающее)
-F: Сброс правил в цепочке (iptables -F INPUT)
-N: Создание цепочки (iptables -N CHAINNEW)
-X: Удаление цепочки (iptables -X CHAINNEW)
-P: Определение правила по умолчанию (iptables -P INPUT DROP)

2. Условия
-p: Сетевой протокол. Допустимые варианты — TCP, UDP, ICMP или ALL. (iptables -A INPUT -p tcp -j ACCEPT – разрешить все входящие tcp-соединения)
-s: Адрес источника — имя хоста, IP-адрес или подсеть. (iptables -A INPUT -s 192.168.0.50 -j DROP – запретить входящие с узла 192.168.0.50)
-d: Адрес назначения. Принцип использования аналогичен предыдущему ключу -s. (iptables -A OUTPUT -d 192.168.0.50 -j DROP – запретить исходящие на узел 192.168.0.50)
-i: Сетевой адаптер, через который приходят пакеты (INPUT) (iptables -A INPUT -i eth2 -j DROP – запретить входящие для Ethernet-интерфейса eth2)
-o: Сетевой адаптер, с которого уходят пакеты (OUTPUT) (iptables -A OUTPUT -o eth3 -j ACCEPT – разрешить исходящие с Ethernet-интерфейса eth3)
--dport: Порт назначения (iptables -A INPUT -p tcp --dport 80 -j ACCEPT – разрешить входящие на порт 80)
--sport: Порт источника (iptables -A INPUT -p tcp --sport 1023 -j DROP – запретить входящие с порта 1023)
-m: Включает дополнительные модули (iptables -A INPUT -p tcp -m multiport --dport 22,80,443 -j ACCEPT – разрешить вхдящие на порты 22, 80, 443)

3. Опции, с помощью которых можно получить информацию
-L: показывает правила в цепочке или всех цепочках. по умолчанию покажет таблицу filter
-n: покажет параметры правила в числовом виде, например, порт будет не http, а 80
-v: выводит более подробную информацию
-V: покажет версию iptables
--line-numbers: покажет номера правил


