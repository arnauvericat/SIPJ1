# MONITORITZACIÓ, CONNEXIÓ REMOTA I LLICENCIAMENT


**##Teoria MONITORTIZACIÓ**

logger[opcions][-p prioritat][missatge]

logger -i -s -p mail.err Aturant el sistema

Server.prioritat accio

**Serveis**
  
- **auth**
- **mail**
- **lpr**
- **cron**
- **kern**

**Prioritats dels serveis**


Prioritat de menos a més important, per exemple si posem Mail.alert ---> sera que la prioritat sera del nivell cap a dalt, soigue de alert a emerg,panic.
Si fiques Mail.=alert sera sol aquesta. SI fiquem *.crit es per a tots

- **debug**
- **infor**
- **notice**
- **warning,warn**
- **err,error**
- **crit**
- **alert**
- **emerg,panic**

-----------------------------------------------------------------------

Explicar una mica aixó la monitoritzacio i després entrar per exemple al firefox i mirar que consumeix, la prioritat, etc.

- El que veem en les següents imatges es la motorització dels processos del sistema en temps real. En la primera veiem tots els processos, aqui podem veure que es el que consumeixen, si un procés no respon, es pot matar. També podem veure la prioritat, per exemple si volem descarregar algo, li podem canviar la prioritat i destinar tots els recursos o no al procés.
  
- En la segona imatge, veiem cuanta RAM s'esta utilitzant, les xarxa d'internet, quantes dades envia i rep.

- EN la última, veiem les particions que té els discs i el que ocupen.

<img width="730" height="486" alt="image" src="https://github.com/user-attachments/assets/11ceeb0d-5bda-452e-84cb-884c0f2baa68" />

<img width="733" height="490" alt="image" src="https://github.com/user-attachments/assets/861e35cc-659e-4f2d-b5bb-520c1dfce3b2" />


<img width="660" height="526" alt="image" src="https://github.com/user-attachments/assets/a22a0dea-2996-4a66-badd-dc10e91056c3" />


**LOGS**

- Entrar als LOGS ---> cd /var/log i després un ls

QUE VEIEM?

- Aqui entrem al directori on contenen tots els tipus de logs del sistema, inclús errors i també la rotació de logs. Però, no es que es guardin tots els logs en general, sinó que es veuen diferents tipus de logs, per exemple també hi ha els logs d'instal·lació de paquets, intents d'autentificació, informació de l'arrancada del sistema. Però on realment es guarden tots tots els logs, es al syslog. Per tant, el que es fa aqui es tenir un registre de la monitorització del sistema, pero des del terminal.

<img width="661" height="329" alt="image" src="https://github.com/user-attachments/assets/3439f1c6-bea1-425b-814f-9c2bb1df61b9" />


quan trobem dmesg.1.gz i els altres això significa que es la rotació de logs, va guardant logs i va  Dintre de nano /etc/logrotate.conf podem decidir el temps de rotació de logs dels serveis en general.

Amb cd /etc/logrotate.d/ serveix per si es vol canviar la rotació dels logs fent el canvi de manera personalitzada de la rotació crean un arxiu i personalitzant-lo


-Obrim dos terminals

- Amb aquesta commanda, podem fer proves forçant logs:

<img width="724" height="262" alt="image" src="https://github.com/user-attachments/assets/d7365d4b-c2e5-4f2f-bb61-a1a4eaf950ca" />

- Després amb l'altra terminal entrem a aquest axriu:

<img width="599" height="47" alt="image" src="https://github.com/user-attachments/assets/3049a3e1-b16b-4575-8d3b-da5368c9c1ef" />

Aqui amb el *.* decidim que tot anirà al syslog 

<img width="598" height="31" alt="image" src="https://github.com/user-attachments/assets/9b150846-c9ec-4564-87d2-cac41d65f1dc" />

- Creem una prova
 
<img width="795" height="606" alt="image" src="https://github.com/user-attachments/assets/dee09f2b-1d02-4894-9eee-399bf1ba327d" />

- entrem al rsyslog i li canviem la prioritat al mail i despres reiniciem el syslog

<img width="795" height="292" alt="image" src="https://github.com/user-attachments/assets/cd8a3bd4-a3ed-44a7-9fd1-8e63ce77f8d3" />

<img width="795" height="292" alt="image" src="https://github.com/user-attachments/assets/47eb2a92-14ec-488d-92ef-3c0f22e5fdf2" />

- Ara fem la prova i al cat mail.log no tindria que sortir el canvi, pero al syslog si:

<img width="775" height="419" alt="image" src="https://github.com/user-attachments/assets/79b4f521-16d4-446d-bc93-15582093f119" />

- Ara cambien a mail.=crit, reiniciem el syslog  i fem la prova i solament al mail.log se veura el de la prioritat crit els altres sol al syslog per tant sol veura el 7 , el 5 i 6 sol al syslog

<img width="758" height="299" alt="image" src="https://github.com/user-attachments/assets/e4a22612-a512-470f-9741-717d9187ffc0" />

<img width="758" height="572" alt="image" src="https://github.com/user-attachments/assets/6e839e4c-9906-4309-9b4f-b318a5b1a7b0" />

- ara agregem aquesta commanda primera i reiniciem syslog, al crear el aitor.log nou, farem una prova amb diferents prioritats:

<img width="722" height="83" alt="image" src="https://github.com/user-attachments/assets/db28b764-87e3-440b-addd-3b34c6cc6455" />

<img width="805" height="451" alt="image" src="https://github.com/user-attachments/assets/ee35c4c4-6898-453f-8329-1d0dd93deac4" />


**Exercici**: simular servidor de logs centralitzat, a una maquina actuara com a srver i l'altra rebra logs del client

**Part server**

- Primer que tot, obro la maquina que simula el server i poso nano /etc/rsyslog.conf i es descomenten aquestes dos linies i després reiniciem amb systemctl restart syslog:
  
<img width="825" height="87" alt="image" src="https://github.com/user-attachments/assets/9a81e49f-bb00-4904-a205-5cf4de02f894" />

- mirem la ip del server en 1p a:

<img width="909" height="149" alt="image" src="https://github.com/user-attachments/assets/7a29918b-a524-4b1b-9af2-a649f4e60c53" />


**Part Client**

- Ara entrem --> nano /etc/rsyslog.d/50-default.conf, i al final de tot posem *.* la ip del server:514 (que son els ports que hem obert junt amb la ip que apuntarà)

<img width="909" height="412" alt="image" src="https://github.com/user-attachments/assets/e71bd7ce-c841-47f4-a9fd-aa8a7e928316" />

- Ara reiniciem systemctl restart syslog.

- Per últim farem una prova ---> farem una prova amb logger -i -s -p cron.alert dient que aquest SI que tindria que sortir, i a la màquina del server fem un tail del syslog per veure si ens surt el log amb l'avis del servei:

<img width="1625" height="831" alt="image" src="https://github.com/user-attachments/assets/c47e0f37-970b-4c49-8fa7-2de9d73dc95b" />

- Veem que surt el log correctament al servidor, fem una altra prova:

<img width="1784" height="402" alt="image" src="https://github.com/user-attachments/assets/9baaff45-fedd-4ada-8ae7-5286d8ff26ed" />


**CONNEXIÓ REMOTA**

- Primer que tot, ens hem de descarregar aquests dos arxius de VNC VIEWER, un ens servirà per a la part client i l'altre per a la part servidor, però sinó fem apt install
tightvncserver :

<img width="763" height="231" alt="image" src="https://github.com/user-attachments/assets/c54fd68b-74ef-4fb9-ae74-ee3b570e3e8e" />

**Part server**

-Fem un sudo dpkg -i del arxiu de la part servidor:

<img width="1033" height="445" alt="image" src="https://github.com/user-attachments/assets/e0a04f62-c7e4-4bc7-88d2-f8744781b3f0" />

- Posem aquestes dues commandes: sudo systemctl enable vncserver-x11-serviced i sudo systemctl start vncserver-x11-serviced per tal d'activar el servidor

<img width="751" height="94" alt="image" src="https://github.com/user-attachments/assets/10a2fe38-8354-4eab-999e-c82e0806c3d9" />

**Part client**

- ens hem de descarregar VNC VIEWER, que ens servirà per a la part client:

<img width="760" height="184" alt="image" src="https://github.com/user-attachments/assets/ba09ae20-39f3-41b0-96a6-102b21b595c5" />

---------------

- Ara per a que funcioni desde la arxa NAT que tenim crearem una clau SSH al **servidor**, primer un update, després apt install openssh-server:

<img width="761" height="265" alt="image" src="https://github.com/user-attachments/assets/5a0c9f11-5a31-43ca-a41c-5b90e85e54d9" />

- Ara tenim que mirar la ip del nostre servidor amb ip a que es 10.0.2.15 i obrim el **client** i comprove que va un ping al server:

<img width="881" height="173" alt="image" src="https://github.com/user-attachments/assets/19fb46f4-c710-4f35-a61f-b3bb97953347" />

- A partir de que tenim una connexió fem: ssh aitor@10.0.2.15 per a que conegui i reconegui el servidor

<img width="737" height="153" alt="image" src="https://github.com/user-attachments/assets/68947007-8d10-47d7-88f2-4fff85a8ee4d" />

- Ara creem el tunel amb ssh:

<img width="737" height="435" alt="image" src="https://github.com/user-attachments/assets/300661aa-e5d7-4f0e-9830-b9f63900d838" />










  


