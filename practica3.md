Consultas DNS Realizadas
### 1. Consulta básica de danielcastelao.org

Realiza una consulta "dig danielcastelao.org" e identifica cada parte de la respuesta.

La consulta realizada fue:

dig danielcastelao.org

### Respuesta:

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

### Explicación de las secciones:

    QUERY SECTION: Muestra la consulta realizada.
    ANSWER SECTION: La respuesta del servidor DNS, incluyendo el registro A que devuelve la IP 178.211.133.37.
    HEADER: Información sobre el estado de la consulta (en este caso, NOERROR).
    TTL: Tiempo de vida del registro (900 segundos).

### 2. Consultas de moodle.danielcastelao.org y www.danielcastelao.org

Compara las respuestas de estas consultas DNS.

Primero, se realiza la consulta a moodle.danielcastelao.org:

dig moodle.danielcastelao.org

### Respuesta:

;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 51703
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

Explicación: moodle.danielcastelao.org no existe (NXDOMAIN).
### 3. Servidores DNS Autoritativos de danielcastelao.org

Para obtener los servidores DNS autoritativos de danielcastelao.org, se realizó la consulta:

dig NS danielcastelao.org

### Respuesta:

;; ANSWER SECTION:
danielcastelao.org.	900	IN	NS	ns2.hover.com.
danielcastelao.org.	900	IN	NS	ns1.hover.com.

    Servidores DNS Autoritativos:
        ns1.hover.com
        ns2.hover.com

Para obtener las IPs de los servidores DNS autoritativos, realizamos consultas adicionales a sus registros A:

dig A ns1.danielcastelao.org

ns1.hover.com.	6593	IN	A	216.40.47.26

dig A ns2.danielcastelao.org

ns2.hover.com.	7200	IN	A	64.98.148.13

### 4. Consulta de Nombres Inversos

Se realizó la consulta de nombres inversos para varias direcciones IP.

    Para la IP 130.206.164.68:

dig -x 130.206.164.68

### Respuesta:

PTR	s164m68.unavarra.es.
PTR	pluto.tlm.unavarra.es.

    Para la IP 8.8.8.8 (DNS de Google):

dig -x 8.8.8.8

Respuesta:

PTR	dns.google.

    Para la IP 9.9.9.9 (DNS de Quad9):

dig -x 9.9.9.9

Respuesta:

PTR	dns9.quad9.net.

### 5. Consulta del Registro SOA de moodle.danielcastelao.org

    Consulta al servidor DNS de Google:

dig @8.8.8.8 SOA moodle.danielcastelao.org

### Respuesta:

;; AUTHORITY SECTION:
danielcastelao.org.	300	IN	SOA	ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300

###     Consulta al servidor primario del dominio:

dig @ns1.hover.com SOA moodle.danielcastelao.org

Respuesta:

;; AUTHORITY SECTION:
danielcastelao.org.	300	IN	SOA	ns1.hover.com. dnsmaster.hover.com. 1720467415 1800 900 604800 300

### 6. Consulta de la IP de www.elpais.com y TTL

Realizamos la consulta para obtener la IP de www.elpais.com:

dig www.elpais.com

### Respuesta:

www.elpais.com.		259	IN	CNAME	prisa-us-eu.map.fastly.net.
prisa-us-eu.map.fastly.net. 16	IN	A	199.232.198.133
prisa-us-eu.map.fastly.net. 16	IN	A	199.232.194.133

La dirección IP de www.elpais.com es 199.232.194.133. El tiempo de vida del registro (TTL) es de 259 segundos.

### 7. Consulta del TTL de diferentes dominios

Realizamos consultas a varios dominios para observar los tiempos de vida (TTL).

    Para el dominio marca.es:

dig marca.es

### Respuesta:

marca.es.		300	IN	A	193.110.128.199

El TTL es de 300 segundos.

    Para el dominio amazon.com:

dig amazon.com

### Respuesta:

amazon.com.		669	IN	A	52.94.236.248
amazon.com.		669	IN	A	54.239.28.85
amazon.com.		669	IN	A	205.251.242.103

El TTL es de 669 segundos.

### 8. Determinación del TTL máximo de un dominio

Para amazon.com, el TTL máximo es de 669 segundos.

### 9. Consulta de la cantidad de máquinas detrás de www.google.es

Realizamos la consulta para obtener las IPs detrás de www.google.es:

dig www.google.es

### Respuesta:

www.google.es.		57	IN	A	142.250.200.131

En este caso, solo aparece una IP. Sin embargo, este no es siempre el caso; puede haber múltiples servidores distribuidos detrás de un dominio como google.es.

### 10. Consulta a un servidor raíz (J.ROOTSERVERS.NET)

Se consultó el servidor raíz J.ROOTSERVERS.NET para ver si acepta el modo recursivo:

dig @J.ROOTSERVERS.NET www.danielcastelao.org

### Respuesta:

J.ROOTSERVERS.NET.	3600	IN	A	15.197.204.56
J.ROOTSERVERS.NET.	3600	IN	A	3.33.243.145

En la respuesta, el flag ra indica que el servidor acepta recursión.

### 11. Visualización de todas las consultas realizadas por un servidor DNS

Para ver todas las consultas realizadas por un servidor DNS, puedes utilizar la herramienta tcpdump:

sudo tcpdump -i any port 53

### 12. Consulta de los servidores de correo (MX) de danielcastelao.org

Se realizó la consulta de los servidores de correo para el dominio danielcastelao.org:

dig MX danielcastelao.org

### Respuesta:

danielcastelao.org.	900	IN	MX	110 aspmx2.googlemail.com.
danielcastelao.org.	900	IN	MX	80 aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	100 alt2.aspmx.l.google.com.
danielcastelao.org.	900	IN	MX	120 aspmx3.googlemail.com.
danielcastelao.org.	900	IN	MX	140 aspmx5.googlemail.com.
danielcastelao.org.	900	IN	MX	130 aspmx4.googlemail.com.
danielcastelao.org.	900	IN	MX	90 alt1.aspmx.l.google.com.

Estos son los servidores de correo responsables de gestionar los correos electrónicos de danielcastelao.org.

### 13. Consulta de registros AAAA para www.facebook.com

Se realizó la consulta de registros AAAA para obtener la dirección IPv6 de www.facebook.com:

dig AAAA www.facebook.com

### Respuesta:

www.facebook.com.	3444	IN	CNAME	star-mini.c10r.facebook.com.
star-mini.c10r.facebook.com. 22	IN	AAAA	2a03:2880:f104:83:face:b00c:0:25de

El registro AAAA devuelve la dirección IPv6 2a03:2880:f104:83:face:b00c:0:25de








