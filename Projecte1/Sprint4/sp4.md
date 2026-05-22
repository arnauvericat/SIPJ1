# MONITORITZACIÓ, CONNEXIÓ REMOTA I LLICENCIAMENT

# Teoria de la monitorització

La monitorització del sistema serveix per controlar l’estat dels serveis, processos i recursos del sistema operatiu. Gràcies a això podem detectar errors, problemes de rendiment o possibles incidències abans que afectin el funcionament del servidor o de l’equip.

Una de les eines més utilitzades per generar logs manualment és la comanda `logger`.

```bash
logger [opcions] [-p prioritat] [missatge]
```

Exemple:

```bash
logger -i -s -p mail.err "Aturant el sistema"
```

Aquesta comanda envia un missatge al sistema de logs amb una prioritat determinada.

La sintaxi general dels logs és:

```bash
servei.prioritat acció
```

## Serveis més habituals

- **auth** → autenticació i accessos
- **mail** → serveis de correu
- **lpr** → impressió
- **cron** → tasques programades
- **kern** → nucli del sistema

---

# Prioritats dels serveis

Les prioritats indiquen la gravetat dels missatges. Van des de missatges informatius fins a errors crítics.

Per exemple:

```bash
mail.alert
```

significa que es registraran els missatges des del nivell `alert` cap amunt (`emerg` i `panic`).

En canvi, si escrivim:

```bash
mail.=alert
```

només es guardaran els missatges exactament del nivell `alert`.

També podem utilitzar:

```bash
*.crit
```

per aplicar-ho a tots els serveis.

## Nivells de prioritat

De menys a més important:

- **debug**
- **info**
- **notice**
- **warning** o **warn**
- **err** o **error**
- **crit**
- **alert**
- **emerg** o **panic**

---

# Monitorització del sistema

La monitorització permet veure en temps real l’estat dels processos i recursos del sistema. Per exemple, podem obrir Firefox i comprovar quanta CPU o memòria RAM està consumint.

A les següents imatges es mostren diferents apartats de monitorització:

- A la primera captura es poden veure tots els processos actius del sistema. Aquí és possible identificar quin procés consumeix més CPU o RAM, modificar la seva prioritat o finalitzar-lo si deixa de respondre.

- A la segona imatge apareix informació relacionada amb la memòria RAM, l’activitat de la xarxa i la quantitat de dades enviades i rebudes.

- A la tercera captura es mostren les particions dels discs i l’espai utilitzat en cadascuna.

<img width="730" height="486" alt="image" src="https://github.com/user-attachments/assets/11ceeb0d-5bda-452e-84cb-884c0f2baa68" />

<img width="733" height="490" alt="image" src="https://github.com/user-attachments/assets/861e35cc-659e-4f2d-b5bb-520c1dfce3b2" />

<img width="660" height="526" alt="image" src="https://github.com/user-attachments/assets/a22a0dea-2996-4a66-badd-dc10e91056c3" />

---

# LOGS DEL SISTEMA

Per accedir als logs del sistema:

```bash
cd /var/log
ls
```

## Què trobem dins `/var/log`?

En aquest directori es guarden diferents registres del sistema operatiu. Aquí podem trobar:

- Errors del sistema
- Registres d’autenticació
- Informació de l’arrencada
- Instal·lació de paquets
- Activitat dels serveis
- Rotació de logs

El fitxer principal on es centralitzen la majoria dels registres és el `syslog`.

Per tant, aquesta carpeta permet consultar tota la informació relacionada amb la monitorització i activitat del sistema des del terminal.

<img width="661" height="329" alt="image" src="https://github.com/user-attachments/assets/3439f1c6-bea1-425b-814f-9c2bb1df61b9" />

---

# Rotació de logs

Quan apareixen fitxers com:

```bash
dmesg.1.gz
```

significa que s’està aplicant una rotació de logs. El sistema guarda versions antigues comprimides per evitar que ocupin massa espai.

El fitxer principal de configuració és:

```bash
nano /etc/logrotate.conf
```

Aquí podem configurar cada quant temps es roten els logs.

També existeix el directori:

```bash
cd /etc/logrotate.d/
```

que serveix per crear configuracions personalitzades per a serveis específics.

---

# Proves amb logs

Primer obrim dos terminals.

Amb aquesta comanda podem generar logs manualment:

<img width="972" height="377" alt="image" src="https://github.com/user-attachments/assets/86f54d41-d4c2-48cf-8417-977745db3bd2" />

A l’altre terminal entrem a l’arxiu de configuració:

<img width="963" height="72" alt="image" src="https://github.com/user-attachments/assets/7c29cd01-5530-440e-97c1-11779a6fe706" />

Amb:

```bash
*.*
```

indiquem que tots els serveis i prioritats es guardaran al `syslog`.

<img width="598" height="31" alt="image" src="https://github.com/user-attachments/assets/9b150846-c9ec-4564-87d2-cac41d65f1dc" />

---

# Creació d’una prova

<img width="765" height="619" alt="image" src="https://github.com/user-attachments/assets/870af2c4-a3c5-4271-8abf-ffddea78c5ae" />

---

# Modificació de prioritats al rsyslog

Entrem a la configuració del `rsyslog`, canviem la prioritat del servei `mail` i reiniciem el servei:

<img width="689" height="272" alt="image" src="https://github.com/user-attachments/assets/b468e1b4-7070-4f6d-b6e1-1d0d9e1d961b" />

<img width="689" height="272" alt="image" src="https://github.com/user-attachments/assets/7343a733-249c-4698-ae76-6e1110747eec" />

Després fem una prova. Els missatges no haurien d’aparèixer a `mail.log`, però sí a `syslog`.

<img width="694" height="391" alt="image" src="https://github.com/user-attachments/assets/7a2f7693-e696-4917-ba62-9d9ac53f7f24" />

---

Ara canviem la configuració a:

```bash
mail.=crit
```

Reiniciem el servei `syslog` i fem una nova prova.

En aquest cas, només els missatges amb prioritat `crit` apareixeran a `mail.log`. La resta continuaran guardant-se únicament al `syslog`.

<img width="706" height="288" alt="image" src="https://github.com/user-attachments/assets/84820d74-71d1-420d-a768-6e971c799b2e" />

<img width="771" height="622" alt="image" src="https://github.com/user-attachments/assets/95b596ec-92d9-4b69-a417-ef98237888f5" />

---

# Creació d’un log personalitzat

Afegim aquesta configuració i reiniciem `syslog`:

<img width="722" height="83" alt="image" src="https://github.com/user-attachments/assets/db28b764-87e3-440b-addd-3b34c6cc6455" />

Això crearà un nou fitxer anomenat `arnau.log`, on es guardaran els missatges definits.

<img width="951" height="574" alt="image" src="https://github.com/user-attachments/assets/8a4dc053-5719-4134-9b61-eaacd9b409fd" />

---

# Exercici: servidor de logs centralitzat

L’objectiu és simular un servidor centralitzat de logs, on una màquina actuarà com a servidor i una altra enviarà els registres.

---

# Part servidor

Primer obrim la màquina servidor i editem:

```bash
nano /etc/rsyslog.conf
```

Descomentem aquestes línies i reiniciem el servei:

```bash
systemctl restart syslog
```

<img width="825" height="87" alt="image" src="https://github.com/user-attachments/assets/9a81e49f-bb00-4904-a205-5cf4de02f894" />

Després comprovem la IP del servidor amb:

```bash
ip a
```

<img width="794" height="171" alt="image" src="https://github.com/user-attachments/assets/87be802b-fa6e-46aa-b4cf-330d405de6c4" />

---

# Part client

Entrem al fitxer:

```bash
nano /etc/rsyslog.d/50-default.conf
```

Al final afegim:

```bash
*.* @IP_DEL_SERVER:514
```

El port `514` és el port estàndard utilitzat pel servei `syslog`.

<img width="856" height="439" alt="image" src="https://github.com/user-attachments/assets/f09d342a-38d2-498a-aee7-945d1c2522df" />

Després reiniciem el servei:

```bash
systemctl restart syslog
```

---

# Proves de funcionament

Fem una prova enviant un log:

```bash
logger -i -s -p cron.alert "Prova de monitorització"
```

A la màquina servidor executem:

```bash
tail -f /var/log/syslog
```

per comprovar si el missatge arriba correctament.

<img width="1024" height="523" alt="image" src="https://github.com/user-attachments/assets/fe6888c5-5919-4233-94d7-398fd667472f" />

Es pot observar que el log arriba correctament al servidor centralitzat.

Fem una altra prova:

<img width="990" height="224" alt="image" src="https://github.com/user-attachments/assets/dec058aa-29a5-4fe5-9534-b3215187f717" />

---

# CONNEXIÓ REMOTA

Per establir una connexió remota utilitzarem **VNC Viewer**.

Primer descarreguem els paquets necessaris per al client i el servidor. També es pot instal·lar amb:

```bash
apt install tightvncserver
```

<img width="907" height="312" alt="image" src="https://github.com/user-attachments/assets/cf0fff96-d3ed-46ad-86c3-98f87684881d" />

---

# Part servidor

Instal·lem el paquet del servidor:

```bash
sudo dpkg -i nom_del_paquet.deb
```

<img width="747" height="287" alt="image" src="https://github.com/user-attachments/assets/bba4d82b-0190-4a07-9d0b-48b6b5abd55b" />

Activem el servei VNC amb:

```bash
sudo systemctl enable vncserver-x11-serviced
sudo systemctl start vncserver-x11-serviced
```

<img width="1004" height="132" alt="image" src="https://github.com/user-attachments/assets/f3fd0d3b-41f6-4376-8de4-3477be564aa6" />

---

# Part client

Instal·lem **VNC Viewer**, que ens permetrà connectar-nos remotament al servidor.

<img width="988" height="245" alt="image" src="https://github.com/user-attachments/assets/d5db2390-b02f-4646-aa28-ee922f3ca719" />

---

# Accés remot mitjançant SSH

Perquè la connexió funcioni correctament dins de la xarxa NAT, instal·lem el servei SSH al servidor.

Primer actualitzem els repositoris i instal·lem:

```bash
apt update
apt install openssh-server
```

<img width="969" height="352" alt="image" src="https://github.com/user-attachments/assets/bfc599f7-fe04-40dc-96d3-1c3e85fba138" />

Comprovem la IP del servidor amb:

```bash
ip a
```

En aquest cas és `10.0.2.15`.

Des del client comprovem la connectivitat amb:

```bash
ping 10.0.2.15
```

<img width="801" height="201" alt="image" src="https://github.com/user-attachments/assets/a41d5efb-0472-4336-96c6-6120784418c5" />

---

# Primera connexió SSH

Des del client executem:

```bash
ssh arnau@10.0.2.15
```

Això permet que el client conegui i accepti la clau del servidor.

<img width="991" height="222" alt="image" src="https://github.com/user-attachments/assets/be049bd6-1a1f-498b-b7a4-b18149990db1" />

---

# Creació d’un túnel SSH

Finalment, creem el túnel SSH per encapsular la connexió VNC de forma segura.

<img width="960" height="607" alt="image" src="https://github.com/user-attachments/assets/6111d79f-c541-4911-ae1c-382703580a48" />
