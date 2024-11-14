# Consultas DNS realizadas

### 1. Realiza una consulta "dig danielcastelao.org" e identifica cada parte de la respuesta (IN, CNAME, A, QUERY SECTION, ANSWER SECTION, AUTHORITY SECTION, etc)

bash
dig danielcastelao.org

; <<>> DiG 9.11.3-1ubuntu1.18-Ubuntu <<>> danielcastelao.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58059
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;danielcastelao.org.		IN	A

;; ANSWER SECTION:
danielcastelao.org.	900	IN	A	178.211.133.37

;; Query time: 161 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 17:30:00 CEST 2024
;; MSG SIZE  rcvd: 63

### 2. Realiza consultas de los siguientes nombres y identifica las diferencias: moodle.danielcastelao.org, www.danielcastelao.org

dig moodle.danielcastelao.org

; <<>> DiG 9.11.3-1ubuntu1.18-Ubuntu <<>> moodle.danielcastelao.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 51703
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;moodle.danielcastelao.org.	IN	A

;; Query time: 207 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 17:33:48 CEST 2024
;; MSG SIZE  rcvd: 54

moodle.danielcastelao.org:

    No se encuentra el nombre del dominio DNS
    No da respuesta (Answer 0)
>[!NOTE]
>Resumen:     moodle.danielcastelao.org no existe (NXDOMAIN)
> mientras que danielcastelao.org sí existe (NOERROR) y tiene un registro A asociado a una dirección IP.


### 3. Averigua el nombre y IP de los servidores DNS autoritativos de www.danielcastelao.org. ¿Por qué suelen ser 2 servidores autoritativos?

dig NS danielcastelao.org

; <<>> DiG 9.11.3-1ubuntu1.18-Ubuntu <<>> NS danielcastelao.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 1740
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;danielcastelao.org.		IN	NS

;; ANSWER SECTION:
danielcastelao.org.	900	IN	NS	ns2.hover.com.
danielcastelao.org.	900	IN	NS	ns1.hover.com.

>[!NOTE]Nombres de los servidores:
>   ns2.hover.com
>    ns1.hover.com

>[!NOTE]
>IP de los servidores:
>dig A ns1.danielcastelao.org
>ns1.hover.com.	6593	IN	A	216.40.47.26
>ns2.hover.com.	7200	IN	A	64.98.148.13

### 4. Realiza las consultas de nombres inversos: 130.206.164.68 y otras dos IPs que se te ocurran.

dig -x 130.206.164.68

_Direcciones_
68.164.206.130.in-addr.arpa. 7125 IN	PTR	s164m68.unavarra.es.
68.164.206.130.in-addr.arpa. 7125 IN	PTR	pluto.tlm.unavarra.es.

dig -x 8.8.8.8

_Direcciones_
8.8.8.8.in-addr.arpa.	14340	IN	PTR	dns.google.

dig -x 9.9.9.9

_Direcciones_
9.9.9.9.in-addr.arpa.	18340	IN	PTR	dns9.quad9.net.




















### 6-Obtén o rexistro SOA (Start of Authority) do dominio  moodle.danielcastelao.org preguntándolle ó servidor DNS de google e logo preoguntándollo directamente ó servidor primario do dominio danielcastelao.org.


1. Consulta al servidor DNS de Google

    dig @8.8.8.8 SOA moodle.danielcastelao.org

 <<>> DiG 9.11.3-1ubuntu1.18-Ubuntu <<>> @8.8.8.8 SOA moodle.danielcastelao.org


;; AUTHORITY SECTION:
danielcastelao.org.	300	IN	SOA	ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300

;; Query time: 127 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Oct 08 19:54:17 CEST 2024
;; MSG SIZE  rcvd: 113



2. Consulta al servidor primario del dominio

    dig @ns1.hover.com SOA moodle.danielcastelao.org



;; AUTHORITY SECTION:
danielcastelao.org.	300	IN	SOA	ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300

;; Query time: 140 msec
;; SERVER: 216.40.47.26#53(216.40.47.26)
;; WHEN: Tue Oct 08 19:55:29 CEST 2024
;; MSG SIZE  rcvd: 113
















### 7-Consulta a IP de www.elpais.com. Cánto tempo queda almaceado o rexistro de recurso no DNS local?, se preguntas ó DNS local por este recurso, qué observas no TTL do rexistro?

    dig www.elpais.com


www.elpais.com.		259	IN	CNAME	prisa-us-eu.map.fastly.net.
prisa-us-eu.map.fastly.net. 16	IN	A	199.232.198.133
prisa-us-eu.map.fastly.net. 16	IN	A	199.232.194.133

se ve la respuesta a la consulta, es decir, la dirección IP correspondiente a www.elpais.com, que es 199.232.194.133

Tiempo almacenado en el registro-> 259 Segundos





















### 8-Busca o TTL de distintos nomes de dominio de servicios que escollas, a qué se poden deber as diferencias?

    Marca

;; ANSWER SECTION:
marca.es.		300	IN	A	193.110.128.199

;; Query time: 27 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 20:12:40 CEST 2024
;; MSG SIZE  rcvd: 53

    Amazon

;; ANSWER SECTION:
amazon.com.		669	IN	A	52.94.236.248
amazon.com.		669	IN	A	54.239.28.85
amazon.com.		669	IN	A	205.251.242.103

;; Query time: 21 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 20:13:05 CEST 2024
;; MSG SIZE  rcvd: 87






















### 9- Determina o TTL máximo (original) dun nome de dominio.

amazon.com.		669	IN	A	52.94.236.248 -> 669 segundos















### 10- Averigua cántas máquinas con distintas IPs están detrás do dominio web www.google.es, sempre son as mesmas e na mesma orde? por qué?

 una sola IP en la ANSWER SECTION, que en este caso es 142.250.200.131 ,  no siempre son iguales las respuestas

 ;; QUESTION SECTION:
;www.google.es.			IN	A

;; ANSWER SECTION:
www.google.es.		57	IN	A	142.250.200.131

;; Query time: 23 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 20:17:34 CEST 2024
;; MSG SIZE  rcvd: 58


















### 11- Pregunta o mesmo a un server raiz (J.ROOTSERVERS.NET por exemplo) e comproba na resposta se o server acepta o modo recursivo


;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1;; -> ra: esta es la clave: significa Recursion Available, es decir, que el servidor ha procesado la consulta de forma recursiva.


2 IP en la ANSWER SECTION 15.197.204.56 y 3.33.243.145


ANSWER SECTION:
J.ROOTSERVERS.NET.	3600	IN	A	15.197.204.56
J.ROOTSERVERS.NET.	3600	IN	A	3.33.243.145

;; Query time: 89 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 20:19:57 CEST 2024
;; MSG SIZE  rcvd: 78

















### 12-Se queremos ver tóda-las queries que fai o servidor de DNS, qué opción temos que usar? averigua a IP de www.timesonline.co.uk, especifica os pasos dados

    Para ver todas las queries que realiza un servidor DNS, podrías utilizar la herramienta tcpdump
sudo tcpdump -i any port 53


;; ANSWER SECTION:
www.timesonline.co.uk.	300	IN	CNAME	alsop-n.uk.
alsop-n.uk.		59	IN	A	52.208.17.106
alsop-n.uk.		59	IN	A	34.240.28.43
alsop-n.uk.		59	IN	A	54.76.240.177

;; Query time: 42 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 20:23:32 CEST 2024
;; MSG SIZE  rcvd: 120
























### 13-Usando a información dispoñible a traveso do DNS especifica a máquina (nome e IP) ou máquinas que actúan como servers de correo do dominio danielcastelao.org


    christian@christian-VirtualBox:/usr/local/apache2/htdocs$ dig MX danielcastelao.org


Todas estas

;; ANSWER SECTION:
danielcastelao.org.	900	IN	MX	110 aspmx2.googlemail.com.
danielcastelao.org.	900	IN	MX	80 aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	100 alt2.aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	120 aspmx3.googlemail.com.
danielcastelao.org.	900	IN	MX	140 aspmx5.googlemail.com.
danielcastelao.org.	900	IN	MX	130 aspmx4.googlemail.com.
danielcastelao.org.	900	IN	MX	90 alt1.aspmx.l.google.com.



















### 14-Podes obter os rexistros AAAA de www.facebook.com? a qué corresponden?


AAAA (o "quad-A") en DNS proporciona una dirección IPv6 para un dominio.


;; ANSWER SECTION:
www.facebook.com.	3444	IN	CNAME	star-mini.c10r.facebook.com.
star-mini.c10r.facebook.com. 22	IN	AAAA	2a03:2880:f104:83:face:b00c:0:25de

;; Query time: 21 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Oct 08 20:33:16 CEST 2024
;; MSG SIZE  rcvd: 102










