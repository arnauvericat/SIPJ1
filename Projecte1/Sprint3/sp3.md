# SPRINT 3: GESTIÓ DE DOMINIS I ACCESSOS  

INSTAL·LACIÓ DOMINI LDAP I UNIR CLIENT AL DOMINI

El primer pas és establir una IP fixa al servidor perquè els equips clients no perdin la connexió. A la interfície de configuració de xarxa es defineix el mètode manual (IPv4) amb l'adreça `10.0.2.15`, màscara `255.255.255.0` i porta d'enllaç `10.0.2.1`.
<img width="580" height="473" alt="image" src="https://github.com/user-attachments/assets/4d1799b8-099c-4589-b809-963d72cc57b5" />

Edició del fitxer de nom de la màquina local utilitzant l'editor `nano`. Al fitxer `/etc/hostname` es defineix el nom del servidor com a `ubuntuserver`.
<img width="488" height="44" alt="image" src="https://github.com/user-attachments/assets/e3839fc7-9e85-41e3-bc12-1bd5d072defa" />

Edició del fitxer de resolució de noms locals utilitzant `nano`. Al fitxer `/etc/hosts` s'afegeix la línia `10.0.2.15 ubuntuserver.gina.cat ubuntuserver` per vincular la IP amb el nom de domini complet (FQDN).
<img width="487" height="96" alt="image" src="https://github.com/user-attachments/assets/1816ed3f-ccb7-4770-b942-6704b4f39725" />

Abans de reconfigurar, si s'executa la comanda `slapcat` (amb usuari root), podem observar que el directori base creat per defecte està configurat com a `dc=nodomain`.
<img width="475" height="256" alt="image" src="https://github.com/user-attachments/assets/58b625dc-e170-4f61-a5b7-b3e403d06068" />

# Reconfigure-slapd

S'inicia l'assistent per configurar el paquet LDAP (normalment amb `dpkg-reconfigure slapd`). A la primera pantalla que pregunta "Voleu ometre la configuració del servidor OpenLDAP?", cal seleccionar `<No>`.

<img width="848" height="175" alt="image" src="https://github.com/user-attachments/assets/7d4ef823-64fc-4dc8-a1dc-2848ab06d7d1" />

El següent pas de l'assistent demana el nom del domini DNS base per al directori LDAP. S'introdueix `gina.cat`.

<img width="1400" height="176" alt="image" src="https://github.com/user-attachments/assets/537b0add-0d40-4283-976f-d8a547b86415" />

Continuació de l'assistent de reconfiguració i comprovació del directori.

<img width="778" height="177" alt="image" src="https://github.com/user-attachments/assets/eb3f5f5b-3075-4f96-8b0a-b9ca157619af" />

L'assistent sol·licita el nom de l'organització per fer-lo servir al DN base. En el nostre cas, introduïm `gina`.

<img width="760" height="176" alt="image" src="https://github.com/user-attachments/assets/a9aea36d-4870-428c-bc31-57b2d77ec174" />

A continuació, ens demana la creació d'una contrasenya segura per a l'administrador del directori LDAP.

<img width="1069" height="195" alt="image" src="https://github.com/user-attachments/assets/841be554-5aa0-4dab-b8fa-e501d3433242" />

L'assistent demana introduir de nou la contrasenya definida al pas anterior per confirmar que s'ha escrit correctament.

<img width="651" height="181" alt="image" src="https://github.com/user-attachments/assets/15b47a5f-209c-4a92-a31a-3a7a5823a0fc" />

A la pregunta de si desitgem que s'elimini la base de dades en purgar el paquet `slapd`, hem de seleccionar l'opció `<Sí>`.

<img width="497" height="258" alt="image" src="https://github.com/user-attachments/assets/e048ac1b-45b9-414b-b4c7-e063b3b0d7e0" />

Un cop acabada la reconfiguració, tornem a executar la comanda `slapcat`. Ara podem comprovar que l'estructura (DN) s'ha creat correctament associada al nostre domini: `dc=gina,dc=cat`.

<img width="294" height="97" alt="image" src="https://github.com/user-attachments/assets/48d91f29-cbdd-4268-9c4a-545f86bdd3a1" />

Mostra del contingut d'un fitxer LDIF creat per generar la Unitat Organitzativa d'usuaris. S'observen els atributs `dn: ou=users,dc=gina,dc=cat` i `objectClass: organizationalUnit`.

<img width="365" height="371" alt="image" src="https://github.com/user-attachments/assets/8d262b06-9e25-4dfa-b53e-495cb4f99898" />

Mitjançant la comanda `ldapadd`, s'insereixen els diferents fitxers LDIF al directori servidor. Autenticant-nos amb l'administrador del domini (`-D "cn=admin,dc=gina,dc=cat"`) i demanant contrasenya (`-W`), afegim seqüencialment la unitat organitzativa (`uo.ldif`), l'usuari (`usu.ldif`) i el grup (`grup.ldif`).

<img width="944" height="205" alt="image" src="https://github.com/user-attachments/assets/7cbd69ac-9653-446a-aa38-5172cb1d563d" />


# Unir un client al domini ldap

Passem a la màquina client. Per poder unir-la al domini, executem la instal·lació dels paquets d'autenticació necessaris mitjançant la comanda: `apt install libnss-ldap libpam-ldap nscd -y`.

<img width="725" height="27" alt="image" src="https://github.com/user-attachments/assets/db407520-0ee2-466d-b28a-3bd36fb7a723" />

Durant la instal·lació d'aquests paquets, s'obre l'assistent `ldap-auth-config`. El primer que ens demana és la URI del servidor LDAP a on ens hem de connectar. Introduïm la IP del nostre servidor: `ldap://10.0.2.15`.

<img width="853" height="279" alt="image" src="https://github.com/user-attachments/assets/9fcb9dd0-75eb-4297-9842-f636b15f639c" />

Finalment, l'assistent ens demana el nom distingit (DN) de la base de cerca per poder fer les consultes al servidor. Hi posem el domini complet: `dc=gina,dc=cat`.

<img width="837" height="221" alt="image" src="https://github.com/user-attachments/assets/67d6d5d5-fd18-4564-a710-93044906afbe" />
L'assistent sol·licita quina és la versió del protocol LDAP que s'ha d'utilitzar. Seleccionem la versió **3**, que és la més actual i recomanada.

<img width="837" height="221" alt="image" src="https://github.com/user-attachments/assets/e9857d05-80f5-444c-a3d2-067662bd3c3e" />
A l'opció que permet fer que les utilitats de contrasenya (PAM) es comportin com si s'estiguessin canviant contrasenyes locals ("Make local root Database admin"), seleccionem **<Sí>**.

<img width="828" height="242" alt="image" src="https://github.com/user-attachments/assets/c6fd37aa-4688-45e6-8ae6-fb8aaa1bb983" />
L'assistent ens pregunta si la base de dades LDAP requereix login per extreure'n les entrades ("Does the LDAP database require login?"). Per a una configuració normal, seleccionem **<No>**.

<img width="828" height="242" alt="image" src="https://github.com/user-attachments/assets/bc8bff51-68f2-4bce-b594-f49b1aa6770e" />
Definim el compte LDAP privilegiat que s'utilitzarà quan l'usuari root canviï una contrasenya. Hi introduïm el nostre administrador: `cn=admin,dc=gina,dc=cat`.

<img width="553" height="229" alt="image" src="https://github.com/user-attachments/assets/b62aec64-11fc-4a7a-aea3-12f6d7ab01c0" />

Introduïm la contrasenya corresponent al compte d'administrador definit al pas anterior.

<img width="800" height="298" alt="image" src="https://github.com/user-attachments/assets/11571806-caa2-40dd-b5a2-6f9fb145e1fc" />

Ara definim el nom del compte que s'utilitzarà per fer login a la base de dades LDAP. Seguint la nostra configuració, hi tornem a introduir `cn=admin,dc=gina,dc=cat`.

<img width="851" height="234" alt="image" src="https://github.com/user-attachments/assets/34bae554-8fba-4b52-ba7d-2ceed8a79963" />

Finalment, introduïm la contrasenya pertinent per a aquest últim compte configurat.

<img width="719" height="198" alt="image" src="https://github.com/user-attachments/assets/2e7127e0-ce5a-4df1-92d4-85320d45e0b5" />

## Nsswitch.conf
S'edita el fitxer `/etc/nsswitch.conf`. Hem d'afegir la paraula `ldap` al final de les línies `passwd`, `group` i `shadow`. D'aquesta manera, el sistema buscarà els usuaris primer de forma local i després al servidor LDAP.

<img width="696" height="437" alt="image" src="https://github.com/user-attachments/assets/38d6594e-036d-42bc-bfb8-12828d814748" />

Al fitxer `/etc/pam.d/common-session` afegim la línia: `session optional pam_mkhomedir.so skel=/etc/skel umask=022`. Això farà que es creï automàticament el directori personal (home) de l'usuari LDAP el primer cop que iniciï sessió.

<img width="554" height="31" alt="image" src="https://github.com/user-attachments/assets/68be4064-a0ab-4ffb-bae9-b4e79272196c" />
Revisem el fitxer `/etc/pam.d/common-password` per comprovar que l'assistent ha afegit correctament el paràmetre `pam_ldap.so`, encarregat de gestionar les contrasenyes contra el directori.

<img width="841" height="95" alt="image" src="https://github.com/user-attachments/assets/359502f7-ccca-47f5-ba65-89ebe728c7a8" />

Per poder fer login gràficament amb els usuaris LDAP, editem `/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf` i hi afegim la línia `greeter-show-manual-login=true`. Això habilita una casella per escriure manualment el nom d'usuari.

<img width="704" height="84" alt="image" src="https://github.com/user-attachments/assets/07db0f95-0c0b-4463-a092-667d42395d81" />

# Proves
Es realitzen proves des de la consola del client:
* `getent passwd | grep alu1` i `getent group | grep alumnes`: Confirmen que el client llegeix l'usuari i el grup d'LDAP.
* `su alu1`: Iniciem sessió amb l'usuari. Es pot observar com automàticament se li crea el directori `/home/alu1`.
<img width="582" height="114" alt="image" src="https://github.com/user-attachments/assets/d217d225-c639-44e2-b5ba-d5d94a9b1d53" />
Per facilitar la gestió de permisos, es crea un grup anomenat `colors` amb `addgroup colors`. Seguidament, s'hi afegeixen els usuaris `roig` i `groc` fent servir `adduser nom_usuari colors`.

<img width="341" height="62" alt="image" src="https://github.com/user-attachments/assets/70eb18d2-d590-4c90-9d7c-73ba519008e5" />

### Servidor samba

Serveix per a compartir arxius, recursos, impresores, etc. Tambe te autenticació a nivell ldap.

Instal·lació del servidor Samba a la màquina executant `sudo apt install samba`.
  
<img width="711" height="152" alt="image" src="https://github.com/user-attachments/assets/3a02267b-0321-4930-aaac-494303d0c774" />

Es prepara el directori que es compartirà a la xarxa:
* Es crea un fitxer de prova amb `touch hola` dins la carpeta `/proves`.
* S'apliquen permisos totals recursius amb `chmod -R 777 proves`.
* S'assigna la propietat a "nobody" (sense usuari) i "nogroup" amb `chown -R nobody:nogroup proves/` per evitar restriccions locals del sistema operatiu.

<img width="692" height="187" alt="image" src="https://github.com/user-attachments/assets/471bbe62-af35-4bd4-9117-233b7492a059" />

Per poder gestionar els accessos al recurs compartit, es creen usuaris locals:
* Es creen tres usuaris (`blau`, `roig`, `groc`) sense directori ni accés a la shell utilitzant `useradd -M -s /sbin/nologin`. Es pot comprovar la creació fent un `tail -3 /etc/passwd`.
* Se'ls hi assigna una contrasenya de Samba executant `smbpasswd -a nom_usuari` per a cadascun.

<img width="508" height="470" alt="image" src="https://github.com/user-attachments/assets/ca63b010-94a9-4eeb-b9de-a586dc54dd14" />

Es crea un grup per facilitar l'assignació de permisos al recurs:
* Es crea el grup amb `addgroup colors`.
* S'afegeixen els usuaris pertinents executant `adduser roig colors` i `adduser groc colors`.

<img width="446" height="212" alt="image" src="https://github.com/user-attachments/assets/6d4aa067-8909-4b30-93ab-a3dc30572e97" />

Es defineix el recurs compartit afegint aquest bloc al fitxer `/etc/samba/smb.conf`:
* `[proves]`: Nom del recurs compartit.
* `path=/proves`: Ruta local del directori.
* `guest ok = yes`: Permet l'accés a convidats (usuaris no autenticats).
* `direct mask = 0775` i `create mask = 0644`: Defineixen els permisos per defecte per a les carpetes i fitxers que s'hi creïn.
* `browseable = yes`: Fa que el recurs sigui visible a l'explorador de xarxa.
* `read only = no`: Permet l'escriptura (no és només lectura).
* `read list = blau, @colors, guest`: Poden llegir el contingut l'usuari blau, tots els membres del grup colors i els convidats.
* `write list = blau, guest`: Només poden escriure (crear/esborrar) l'usuari blau i els convidats.
* `invalid users = roig`: S'impedeix explícitament l'accés a l'usuari roig.

<img width="446" height="212" alt="image" src="https://github.com/user-attachments/assets/1fac8386-36c0-4ece-b4bf-49d47204341d" />

S'apliquen els canvis de configuració reiniciant els dimonis amb `systemctl restart smbd nmbd`. A continuació, amb `systemctl status smbd nmbd`, es comprova que tant el servei `smbd` (encarregat de les connexions) com l'`nmbd` (encarregat de la resolució de noms NetBIOS) estan actius i corrent.

<img width="881" height="660" alt="image" src="https://github.com/user-attachments/assets/2b6b91fd-aa03-4567-9fd1-7513de26760f" />

### Client samba

Al client, s'instal·len les eines per connectar-se per consola executant `apt install smbclient`. Gràficament, el client ja pot veure la carpeta compartida amb el seu contingut: les subcarpetes "Fortinaiti i la babagi" i "mec", juntament amb el fitxer "hola".

<img width="543" height="22" alt="image" src="https://github.com/user-attachments/assets/a8b23c6e-dafd-4619-b860-11d5a46b68c5" />

Quan s'intenta accedir al recurs des de l'entorn gràfic d'Ubuntu, apareix una finestra demanant credencials (`Cal autenticació`). En introduir l'usuari `roig` i la seva contrasenya, l'accés és denegat. Això confirma que la directiva `invalid users = roig` configurada a l'`smb.conf` funciona correctament (el que a les notes s'indica com "Efectivament no va").

<img width="372" height="97" alt="image" src="https://github.com/user-attachments/assets/b376bbb2-8485-4b47-b710-073ce8fc6642" />

Efectivament no va

<img width="600" height="426" alt="image" src="https://github.com/user-attachments/assets/2f8b6d6b-45b3-48a5-9165-a1476bec3592" />

<img width="600" height="426" alt="image" src="https://github.com/user-attachments/assets/7d9202ab-1ea4-4ae4-ad75-7295cb5ba38f" />


### Servidor NFS

Instal·lació nfs-kernel-server

Iniciem el procés instal·lant el paquet principal del servidor NFS executant la comanda `apt install nfs-kernel-server`.

<img width="729" height="340" alt="image" src="https://github.com/user-attachments/assets/a7c544bf-6c19-41ba-afb1-b28fb2bf1811" />

S'executa la comanda `systemctl status nfs-server` per comprovar l'estat del servei NFS. La sortida per pantalla mostra el missatge `active (exited)` en color verd, confirmant que el servei s'ha iniciat correctament.
<img width="728" height="203" alt="image" src="https://github.com/user-attachments/assets/a22aa9e8-1f75-4983-94cc-60b54de3886c" />

S'executa una seqüència de comandes per preparar el directori a compartir: `mkdir provesNFS` per crear-lo, `chown nobody:nogroup provesNFS/` per assignar-ne el propietari i grup per defecte, i `chmod 777 provesNFS/` per atorgar-li permisos totals. Finalment, s'executa `ls -l | grep proves`, on es verifica visualment que s'han aplicat els permisos `drwxrwxrwx` i el propietari `nobody nogroup`.

<img width="728" height="203" alt="image" src="https://github.com/user-attachments/assets/e33166b8-d82f-43ea-a699-543a5450d7e0" />

Es mostra l'editor de text GNU nano amb el fitxer `/etc/exports` obert. A la darrera línia s'hi ha inserit la directiva `/provesNFS *(rw,sync,no_subtree_check)` per configurar l'exportació del directori a la xarxa.

<img width="730" height="235" alt="image" src="https://github.com/user-attachments/assets/d40aa780-af20-4124-b395-56b50db750ae" />

A la terminal del servidor, s'accedeix al directori compartit amb `cd provesNFS/` i s'executa `touch hola` per crear un fitxer buit. Seguidament s'executa `ls` i es llista únicament el fitxer `hola`.

<img width="366" height="80" alt="image" src="https://github.com/user-attachments/assets/072ce7c3-b5ca-4360-bb1f-78e81205713d" />

Es mostra una execució posterior de la comanda `ls` dins del directori `/provesNFS#` al servidor. El llistat mostra ara dos fitxers: `adeu` i `hola`, confirmant la interacció del client.

<img width="301" height="46" alt="image" src="https://github.com/user-attachments/assets/2e9ddc74-289d-4b52-81e0-6a7462660b25" />

Es mostra el contingut d'un fitxer amb format LDIF (`usu.ldif`) per a la creació de l'usuari `alu2`. S'hi defineixen els paràmetres de l'usuari, incloent-hi la ruta del seu directori personal de xarxa mitjançant la línia `homeDirectory: /perfils/alu2` i el seu identificador `uidNumber: 1033`.

<img width="364" height="256" alt="image" src="https://github.com/user-attachments/assets/a8c5dc74-2553-4b07-a1ca-cd410f430558" />

S'executa la comanda `ldapadd -x -D "cn=admin,dc=gina,dc=cat" -W -f usu.ldif` a la terminal del servidor per inserir l'usuari definit a l'arxiu LDIF dins de la base de dades del directori LDAP.

<img width="728" height="75" alt="image" src="https://github.com/user-attachments/assets/39dd9b73-7022-44f2-9b6b-e992a3a6b581" />


### Client NFS

A la terminal de la màquina client, s'executa la comanda `apt install nfs-common rpcbind` per instal·lar els paquets necessaris que permeten muntar sistemes de fitxers NFS per xarxa.

<img width="733" height="313" alt="image" src="https://github.com/user-attachments/assets/c160abed-9fdf-40e0-96a5-8740e851e067" />

A la màquina client s'accedeix a l'arrel amb `cd /` i s'executa `mkdir divendres` per crear el punt de muntatge local. Tot seguit, s'apliquen permisos totals al directori executant `chmod 777 divendres/`.

<img width="431" height="50" alt="image" src="https://github.com/user-attachments/assets/a5fb86e2-9e34-4423-b985-fce964a435d7" />

Es visualitza una línia de configuració amb els paràmetres de muntatge del recurs compartit per al fitxer `fstab`: `10.0.2.15:provesNFS /divendres nfs auto,noatime,nolock,bg,nfsvers=3,intr,tcp...`
<img width="859" height="28" alt="image" src="https://github.com/user-attachments/assets/167175c5-cc5d-4b5d-aeb7-ed520d530ae2" />

Al client s'accedeix al directori muntat amb `cd divendres/` i s'executa `ls`, mostrant el fitxer `hola` creat prèviament al servidor. A continuació, s'executa `touch adeu` per realitzar una prova d'escriptura a través de la xarxa.

<img width="225" height="25" alt="image" src="https://github.com/user-attachments/assets/7738ae26-c491-4271-96de-7df311e3be17" />

Al client s'eleven els privilegis amb `sudo su`. S'accedeix a l'arrel amb `cd /`, es crea el directori per als perfils d'usuari amb `mkdir perfils` i se li atorguen permisos amb `chmod 777 perfils/`. Finalment, s'inicia l'escriptura de la comanda `nano /etc/` per editar la configuració pertinent.

<img width="424" height="83" alt="image" src="https://github.com/user-attachments/assets/a9b0152f-6219-4f69-9301-3b566ec28282" />

Es visualitza la línia de configuració corresponent al muntatge del directori de perfils d'usuari: `10.0.2.15:perfils /perfils nfs auto,noatime,nolock,bg,nfsvers=3,intr,tcp,actimeo=1800 0 0`.

<img width="403" height="113" alt="image" src="https://github.com/user-attachments/assets/a270c9e8-6d8a-48f2-969a-4b07a79a8cd7" />


<img width="872" height="41" alt="image" src="https://github.com/user-attachments/assets/78aa6299-2270-4c73-af5d-0e0997cbd15a" />
