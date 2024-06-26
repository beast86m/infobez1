***Уязвимости и атаки на информационные системы, Фролов И.Р., SYS-24***

**Задание 1**

скрин с результатом сканирования nmap, на котором видно 23 порта со статусом OPEN:

![изображение](https://github.com/beast86m/infobez1/assets/47268167/eb2b5bbb-a74a-4640-b5aa-0bc386358e12)

ниже ссылки на уязвимости в протоколах:
https://www.exploit-db.com/exploits/19462 - telnet
https://www.exploit-db.com/exploits/1056 - HTTP
https://www.exploit-db.com/exploits/1794 - VNC

**Задание 2**

Режим SYN -sS При использовании данного режима Nmap посылает SYN пакет и для хоста это выглядит как будто с ним хотят установить реальное соединение. Если приходит ответ SYN/ACK – значит порт открыт, а если RST – значит закрыт, если ответ не приходит или пришло ICMP-сообщение об ошибке – значит порт фильтруется.
![изображение](https://github.com/beast86m/infobez1/assets/47268167/b884aa01-ca36-4ca4-b3a9-f0974672b72c)

В режиме FIN nmap начинает FIN-исследование, используя FIN-пакет. Поскольку ранее соединение с исследуемым узлом не было установлено, исследуемый узел отвечает RST-пакетом для сброса соединения. Поступая таким образом, исследуемый узел сообщает о своем существовании.
![изображение](https://github.com/beast86m/infobez1/assets/47268167/ecde50c1-aa53-49dd-ad32-f45b366f8fb4)
![изображение](https://github.com/beast86m/infobez1/assets/47268167/2363713c-990e-40f5-a676-6d4c5c094693)


При таком способе сканирования TCP-пакеты отсылаются с установленными флагами PSH, URG и FIN. Этот тип также ожидает пакеты RST для closed портов. Отправленный пакет не содержит биты SYN, RST или ACK и и в ответ будет отправка RST в случае, если порт закрыт, или не повлечет никакого ответа, если порт открыт. При Xmas устанавливаются FIN, PSH и URG флаги. Если в ответ приходит RST пакет, то порт считается закрытым, отсутствие ответа означает, что порт открыт|фильтруется.
![изображение](https://github.com/beast86m/infobez1/assets/47268167/49fd0ce4-5cbf-4b21-ab30-2d88418febaa)
![изображение](https://github.com/beast86m/infobez1/assets/47268167/87bf6829-90ff-4ec2-9ff0-e5f0b6c8890a)
![изображение](https://github.com/beast86m/infobez1/assets/47268167/b356be44-e61f-49c9-ba45-ac1582671a21)

При DP сканировании утилита позволяет сканировать порты используемые UDP службами и работает путём отправки пустого UDP заголовка на соответствующие порты. Если приходит ошибка “порт недостижим”, то в зависимости от типа ошибки Nmap определяет – порт закрыт или фильтруется, если в ответ пришел UDP – пакет значит порт открыт, а если ответа нет – будет присвоен статус open|filtered. Работает UDP сканирование крайне медленно и для ускорения процесса рекомендуется задать список интересующих портов (например -p U:53).
![изображение](https://github.com/beast86m/infobez1/assets/47268167/80996fdf-8047-46b8-b623-14b1319b9ef7)
![изображение](https://github.com/beast86m/infobez1/assets/47268167/b15c070b-063b-4ab3-b1b6-c01a1eecc819)


