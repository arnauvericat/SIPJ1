---
layout: default
title:Sprint 2: Gestió de la Informació del Sistema i Administració
---

#  **1.Sistemes de fitxer i particions**

## Mida del sector
Un sector és la unitat mínima d’emmagatzematge en un disc o SSD, típicament de 512 bytes o 4 KB, sobre la qual el sistema operatiu pot llegir o escriure dades; s’organitza en pistes i cèrcols i no es pot accedir a fraccions d’un sector.

Amb la comanda dfisk -l podem veure les particions i els discs que tenim al nostre ordinador, aixi podem veure que en el nostre disc tenim 512 bytes en la mida del sector.

<img width="385" height="27" alt="image" src="https://github.com/user-attachments/assets/8cf7cd49-7e15-42a0-924c-110dfe063d33" />

Aquestes comandes ens serveixen per a crear un fitxer de text amb el contingut que hi ha a la imatge, després podem veure que el fitxer conte 17 bytes de dades reals, però sol ocupa 4KB.

<img width="664" height="173" alt="image" src="https://github.com/user-attachments/assets/2072a5a2-b507-4b93-b276-6f845465f488" />

<img width="736" height="422" alt="image" src="https://github.com/user-attachments/assets/dbff9c6c-08ff-41a2-b46c-2c4850b398fe" />



En windows tenim el desfragmentador de discs per a reduir aquesta fragmentació.

###### Foto desfragmentador de windows11


Ambe el cas de Linux no necessita desfragmentador perquè els seus sistemes de fitxers moderns (ext4, XFS, Btrfs) gestionen els blocs de manera intel·ligent, reservant espais contigus i evitant que els fitxers es fragmentin, fins i tot quan creixen. La fragmentació és mínima, només apareix en discos gairebé plens o amb fitxers molt grans.

Igualment aqui veiem una imatge on desfragmentem el disc.

<img width="1435" height="888" alt="image" src="https://github.com/user-attachments/assets/c0efc412-6df3-4b53-a6d0-f884ae3e4adf" />
<img width="1474" height="421" alt="image" src="https://github.com/user-attachments/assets/f354c8e1-0537-4f84-b91d-5a6a142ecdba" />



## Mida del bloc
Un bloc és la mínima unitat d’emmagatzematge d’un sistema de fitxers, normalment de 1 a 8 KB. Els fitxers s’emmagatzemen en blocs contigus per evitar fragmentació. La mida del bloc es tria en crear el sistema de fitxers: blocs grans van bé per fitxers grans i blocs petits per fitxers petits.

<img width="658" height="93" alt="image" src="https://github.com/user-attachments/assets/0e93ba17-f1cb-42d7-8094-9ebc33fa9a63" />
<img width="658" height="93" alt="image" src="https://github.com/user-attachments/assets/b853c98b-1ca9-4546-9054-1cd9faa2f860" />

## Fragmentació interna

La fragmentacio de disc es tot l'espai desaprofitat dintre de la partició.

Per a la fragmentació podem canviar la mida dels sectors en formatar el sistema operatiu, això fara que utilitzem l'espai que hi ha i no perguem lloc, el dolent es que contra mes sectors més lent anirà el sistema operatiu.

## Fragmentació externa

La fragmentació externa es quan l'espai lliure en una memoria o sistema d'emmagatzematge que esta dividit en petits blocs.

# Tipus de Formateig de Discs

## 1. Formateig d’Alt Nivell (High-Level Formatting)
- També conegut com **formateig lògic**.
- Prepara el sistema de fitxers perquè el sistema operatiu pugui emmagatzemar dades.
- **Accions principals:**
  - Crear taula de particions.
  - Instal·lar un sistema de fitxers (FAT, NTFS, ext4, etc.).
  - Assignar directoris i metadades.
- **Exemple:** formatar un pendrive a NTFS o ext4.
- **Objectiu:** que el sistema operatiu pugui llegir i escriure fitxers.

---

## 2. Formateig de Nivell Mitjà (Medium-Level Formatting)
- Pont entre el baix i l’alt nivell; prepara el mitjà sense tocar dades físiques.
- **Accions principals:**
  - Inicialitzar sectors o blocs del disc.
  - Comprovar integritat bàsica.
  - Pot incloure una simulació de formateig de baix nivell en discs moderns.
- **Objectiu:** assegurar que el suport físic és correcte abans del formateig lògic.

---

## 3. Formateig de Baix Nivell (Low-Level Formatting)
- També anomenat **formateig físic**.
- Defineix l’estructura física dels sectors i pistes del disc.
- **Accions principals:**
  - Crear pistes i sectors físics.
  - Establir marques de sincronització i bits de control.
- **Exemple:** discos antics; avui dia els HDD i SSD ja venen preformatats de baix nivell.
- **Objectiu:** preparar el suport físic per al formateig lògic.



## Particions/volums

Una partició de disc és una subdivisió lògica d’un disc dur físic. Bàsicament, és com dividir un disc gran en “seccions” més petites que el sistema operatiu tracta com a unitats independents.

Un volum es una capa d'abstracció que es posa per damunt de les particions.

<img width="269" height="156" alt="image" src="https://github.com/user-attachments/assets/50d32909-7fd7-41fe-9a8b-6fb8cad0e1eb" />

* ## GPARTED

* ### Comandes
 
Amb aquestes comandes que veurem ara farem una particio del disc amb terminal i amb el GPARTED.

Primer mirarem quin es el disc al que li volem fer la partició.
  
<img width="541" height="104" alt="image" src="https://github.com/user-attachments/assets/3137a71c-b5e4-4f8d-88ed-e6af3ed8f8e0" />

Amb la comanda sudo `fdisk /dev/sdb` entrarem al particionador de linux on podrem crear les nostres particions. Després clicarem la `n` per a fer una partició nova, la `p` per a fer una partició primària i crearem la partició amb la mida que vulguem, en aquest cas d'un disc de 10 GB he fet d'aproximadament 5Gb cada partició.


<img width="735" height="215" alt="image" src="https://github.com/user-attachments/assets/7cf3b7a8-0972-4566-9cb7-3ac8230a940c" />

<img width="735" height="215" alt="image" src="https://github.com/user-attachments/assets/f55b6694-506a-4713-8ccc-3453c1f9376c" />

<img width="726" height="203" alt="image" src="https://github.com/user-attachments/assets/7b79f31b-cb14-4060-aa82-0f4d3a5883b6" />

Amb el Gparted crearem l'altra partició de 5Gb, aixo ho podem fer anant a la fulla de l'esquerra i configurant una nova partició.

<img width="768" height="209" alt="image" src="https://github.com/user-attachments/assets/721192fb-0e81-420a-acb8-fc96bf649d65" />

I veirem que la mida del bloc es de 2048 bytes.

<img width="556" height="78" alt="image" src="https://github.com/user-attachments/assets/a96e5301-0ca9-4bd6-a567-26a96e28914e" />

En aquesta imatge es pot veure que s’executa la comanda mount -t ext4 /dev/sdb1 /mnt/particio1/, que serveix per muntar la partició /dev/sdb1 al directori /mnt/particio1 utilitzant el sistema de fitxers ext4. També es pot veure que s’entra al directori muntat i es llista el seu contingut, on apareix el directori lost+found, típic dels sistemes ext4. A continuació es crea un fitxer anomenat prova amb touch prova i després es comprova amb ls que el fitxer efectivament es troba dins del punt de muntatge, demostrant que la partició està funcionant en mode lectura i escriptura.

<img width="613" height="95" alt="image" src="https://github.com/user-attachments/assets/2147a87a-b62f-420e-a57c-0f5b2511d91f" />

En aquesta imatge es pot veure que es torna a utilitzar la comanda mount -t ext4 /dev/sdb1 /mnt/particio1/. Un cop muntada la partició, es llista el contingut del directori i tornen a aparèixer lost+found i el fitxer prova. Això confirma que el muntatge manual funciona correctament i que el contingut de la partició es manté accessible després de repetir el procés.

<img width="374" height="62" alt="image" src="https://github.com/user-attachments/assets/935ee461-6458-46a7-b170-9b8d7d2f7b5d" />

En aquesta imatge es pot veure el fitxer de configuració /etc/fstab. A la part inferior s’hi observa una línia que estableix que la partició /dev/sdb1 s’ha de muntar automàticament al directori /mnt/particio1 utilitzant el sistema de fitxers ext4 i amb permisos de lectura i escriptura (rw). Els valors 0 0 indiquen que no es realitzaran comprovacions automàtiques del sistema de fitxers ni còpies amb dump. Aquesta configuració fa que la partició es munte de manera persistent a cada arrencada del sistema.

<img width="612" height="144" alt="image" src="https://github.com/user-attachments/assets/9bd4a661-80de-4656-b5ef-b28cf68221a6" />

En aquesta imatge es pot veure que s’accedeix de nou al directori /mnt/particio1 i se’n llista el contingut. Hi apareixen lost+found i el fitxer prova, cosa que indica que la partició s’ha muntat correctament, tant per la configuració de fstab com pel procés realitzat anteriorment. Això confirma que el muntatge persistent està configurat i funciona com s’esperava.

<img width="725" height="265" alt="image" src="https://github.com/user-attachments/assets/79b65e7e-4ab9-4779-b553-1267767aa103" />

I fem un `ls` per a veure que efectivament surt el que hem creat.

<img width="294" height="46" alt="image" src="https://github.com/user-attachments/assets/9a18a701-5bec-4696-9586-6c70614acb8d" />

3.# Gestió d'usuaris, grups i permisos

En aquesta imatge es pot veure que s’està editant el fitxer /etc/passwd amb l’editor nano. Aquest fitxer conté la llista de tots els comptes d’usuari del sistema, amb informació com el nom d’usuari, l’UID, el GID, el directori personal i la shell assignada. Es poden observar entrades del sistema com root, daemon, bin, sys, i moltes altres associades a serveis del sistema, totes amb la shell configurada com /usr/sbin/nologin per evitar que iniciïn sessió. També es veu un usuari final amb UID 1000 que té com a shell /bin/bash, i per tant és un compte real amb capacitat d’inici de sessió. Aquest fitxer serveix principalment com a base de dades visible d’usuaris del sistema.

<img width="1201" height="698" alt="image" src="https://github.com/user-attachments/assets/57848529-7400-455e-b369-a96a3338b95d" />

En aquesta imatge es pot veure que s’està editant el fitxer /etc/group. Aquest fitxer mostra tots els grups del sistema, amb el seu nom, GID i els membres que en formen part. Aquí apareixen grups com root, daemon, adm, cdrom, sudo, audio, video, lp, entre molts altres. També es pot veure que alguns grups tenen com a membres usuaris específics, com per exemple grups on apareix l’usuari principal associat a funcions del sistema, com ara el grup sudo per elevar permisos o el grup adm per accedir a logs. Aquest fitxer és fonamental per controlar permisos col·lectius, ja que determina quins usuaris tenen accés compartit a determinats recursos.

<img width="1205" height="713" alt="image" src="https://github.com/user-attachments/assets/ce434aac-c401-481d-92ee-55bd4997de0a" />

En aquesta imatge es pot veure que s’edita el fitxer /etc/shadow, que conté les contrasenyes encriptades dels usuaris. Les entrades mostren el nom d’usuari i, en lloc de la contrasenya real, una cadena encriptada o símbols com * o !, que bloquegen l’inici de sessió. A continuació hi ha informació addicional com dates d’últim canvi de contrasenya, caducitat, o períodes d’inactivitat. La presència de valors com 19750 o 99999 indica la forma en què el sistema controla la validesa de la contrasenya. Aquest fitxer és molt sensible i només pot ser llegit per root, ja que conté informació crítica per a la seguretat del sistema.

<img width="1205" height="713" alt="image" src="https://github.com/user-attachments/assets/395232d9-f102-4f1b-aa94-dab4fb55cb66" />

En aquesta imatge es pot veure el fitxer /etc/gshadow, que és l’equivalent del fitxer group però amb la informació sensible de contrasenyes de grups i membres administradors dels grups. Aquí es mostren grups com root, daemon, adm, sudo, audio, video, disk, i molts més, amb els seus membres assignats. Igual que amb /etc/shadow, les contrasenyes de grup estan encriptades o bloquejades amb símbols, i s’hi poden definir usuaris administradors del grup. Aquest fitxer proporciona una capa de seguretat afegida als grups, controlant qui pot modificar la seva composició.

<img width="1205" height="713" alt="image" src="https://github.com/user-attachments/assets/c1c979c1-f723-4321-b536-19ef3a17c191" />

Utilitzem la comanda modular per crear un usuari anomenat xina, aquesta comanda crea automàticament l'usuari amb UID 1001 i el grup amb GID 1001, genera el directori personal a /home/xina i copia els fitxers des de /etc/skel, el sistema demana establir una contrasenya però dona error per no introduir-ne cap, després demana informació addicional com nom complet i telèfons que es deixen buits, i finalment es confirma que la informació és correcta.

<img width="537" height="381" alt="image" src="https://github.com/user-attachments/assets/0f830fa8-e299-45b3-9509-e2991572f41d" />

Consultem el fitxer /etc/passwd amb la comanda cat i grep per buscar l'usuari gina, es mostra la informació de l'usuari gina que té UID 1002 i GID 1002, el seu directori personal està configurat a /home/gina i utilitza /bin/bash com a shell per defecte

<img width="397" height="39" alt="image" src="https://github.com/user-attachments/assets/feb37c0f-3e3b-4aa9-88a0-00c1671ce389" />

Llistem el contingut del directori /home/gina amb ls, es mostren les carpetes estàndard Desktop Documents Downloads Music Pictures Public snap Templates i Videos que són les carpetes bàsiques d'un usuari.

<img width="731" height="44" alt="image" src="https://github.com/user-attachments/assets/de60d0d6-044f-4862-a09f-dba1a3fb5d37" />

Consultem el fitxer /etc/passwd per l'usuari casper, es mostra que té UID 1003 i GID 1003, el directori personal és /home/casper i utilitza /bin/sh com a shell inicial.

<img width="511" height="41" alt="image" src="https://github.com/user-attachments/assets/15c9c37f-5bad-4ff9-9ee9-35e33abfc98b" />

Consultem el fitxer /etc/group per buscar el grup casper que té GID 1003, canviem la contrasenya de l'usuari casper amb passwd, el sistema requereix contrasenya de 8 caràcters i s'actualitza correctament.

<img width="511" height="41" alt="image" src="https://github.com/user-attachments/assets/585a3b5c-8ceb-4dc3-b3fa-d3c615ec8b99" />

Modifiquem la shell de casper amb usermod -s /bin/bash canviant de /bin/sh a /bin/bash, creem el directori personal amb mkdir casper, llistem els directoris d'usuari a /home amb ls -l on es veuen arnau casper gina i xina amb els seus propietaris i permisos, i finalment l'usuari casper ja pot accedir amb el nou shell.

<img width="526" height="94" alt="image" src="https://github.com/user-attachments/assets/5e0c84e2-1cd9-4326-a5db-44030b3c170b" />

Veiem el contingut del directori /home amb la comanda ls -l on es llisten tots els usuaris del sistema arnau casper gina i xina cadascú amb el seu propi directori i permisos corresponents observem que l'usuari xina apareix amb identificadors numèrics 1001 en lloc del seu nom i a sota es mostra que l'usuari casper ha iniciat sessió al sistema.

<img width="444" height="41" alt="image" src="https://github.com/user-attachments/assets/280b2fed-fe76-497f-9eea-fc5dc89d11b8" />

Es llisten els directoris del sistema amb ls i es veuen diversos usuaris incloent prova4 que serà eliminat s'utilitza la comanda deluser per eliminar l'usuari prova4 el sistema mostra un advertiment que el grup prova4 ja no té membres però l'eliminació es completa correctament.

<img width="481" height="110" alt="image" src="https://github.com/user-attachments/assets/9e0c5ec0-38ad-4b1b-b218-3dc60e9a15b1" />

S'intenta eliminar l'usuari prova3 amb userdel -r però el sistema no troba el directori de correu d'aquest usuari després de l'eliminació es llisten els directoris i es comprova que prova3 ha desaparegut però prova4 encara apareix al llistat.

<img width="734" height="106" alt="image" src="https://github.com/user-attachments/assets/ff534e70-2dae-4ba1-b0cd-b8db51ebcc6b" />

Es consulta el fitxer /etc/shadow per veure la informació de contrasenya de prova2 es mostra la contrasenya encriptada i les dates de caducitat després s'utilitza usermod -L per bloquejar el compte de prova2 però sembla que hi ha algun error en la execució ja que es torna a consultar i la contrasenya apareix igual.


<img width="520" height="151" alt="image" src="https://github.com/user-attachments/assets/58318732-0275-4208-87c8-94ddce89e015" />

S'afegeix l'usuari prova2 al grup proves amb adduser prova2 proves la operació es realitza correctament després s'intenta afegir prova3 al mateix grup amb gpasswd però prova3 ja no existeix al sistema.

<img width="536" height="77" alt="image" src="https://github.com/user-attachments/assets/62b11c66-b800-4462-bcf6-2c534e2ba2a1" />

Es modifica la informació de l'usuari prova4 amb usermod afegint el comentari proves després es consulta repetidament el fitxer /etc/passwd per veure els usuaris prova2 i prova4 però hi ha línies duplicades en els resultats.

<img width="907" height="97" alt="image" src="https://github.com/user-attachments/assets/eb5175fd-8175-440b-bb1d-894b12d06cd3" />

Es consulta el grup proves al fitxer /etc/group i es veu que prova2 n'és membre s'intenta eliminar el grup proves amb groupdel però falla perquè prova4 encara té aquest grup com a grup principal s'utilitza usermod per canviar el grup principal de prova4 i llavors sí que es pot eliminar el grup proves.

<img width="902" height="65" alt="image" src="https://github.com/user-attachments/assets/6b9205ff-094b-45d8-8185-be1e19476af9" />

Es treu l'usuari prova4 del grup proves amb deluser i també s'intenta treure prova3 amb gpasswd -d però prova3 ja no existeix finalment es consulta el grup proves i ja no apareix a la llista.

<img width="421" height="216" alt="image" src="https://github.com/user-attachments/assets/c68e61a2-bd1b-46e9-b5a6-fa50ba6193da" />

S'estableix el grup proves com a grup principal de prova4 amb usermod -g i es verifica amb groups prova4 que ara pertany als grups proves i users.

<img width="435" height="151" alt="image" src="https://github.com/user-attachments/assets/7919c607-dd30-436c-98d9-16e7b2a7ea3a" />

Treiem l'usuari prova4 del grup proves amb una comanda que sembla estar mal escrita però la operació funciona igualment. Després intentem treure l'usuari prova3 del mateix grup però com que prova3 ja no existeix al sistema no podem fer-ho. Quan mirem el fitxer /etc/group veiem que el grup proves encara té l'usuari prova2 dins.

<img width="434" height="46" alt="image" src="https://github.com/user-attachments/assets/5c1e7d97-b114-4c33-9ac4-2a02689cbe2f" />

 Canviem el grup principal de l'usuari prova4 perquè sigui proves amb la comanda usermod. Quan comprovem el fitxer /etc/passwd veiem que prova4 ara té el número de grup 1007 que correspon al grup proves.
 
<img width="434" height="23" alt="image" src="https://github.com/user-attachments/assets/6db9c054-a8b4-4b3a-85aa-4078bc3f66c1" />

 Intentem eliminar un grup anomenat prove però no existeix. Després fem que prova4 tingui com a grup principal el seu propi nom d'usuari. Tornem a intentar eliminar el grup prove sense sort i quan mirem el grup proves encara segueix existint.
 
<img width="428" height="43" alt="image" src="https://github.com/user-attachments/assets/4dd084f7-c4f8-40a2-9a95-3ecf6bf0a214" />

Mirem la configuració del fitxer /etc/adduser.conf on veiem els paràmetres del sistema. La configuració diu que els directoris dels usuaris aniran a /var en lloc de /home. Les opcions per crear directoris per grups o per lletra inicial estan desactivades. Els fitxers que es copien als nous usuaris estan a /etc/skel. També veiem els números que s'assignen automàticament als usuaris i grups del sistema.

<img width="302" height="39" alt="image" src="https://github.com/user-attachments/assets/e8d7efa7-bbdb-4470-8df5-5eae92ef5230" />

 Llistem el que hi ha dins del directori /var i veiem totes les carpetes del sistema juntament amb una carpeta prova5. Consultem la contrasenya de l'usuari prova5 al fitxer /etc/shadow i veiem que té configurada una data de caducitat.
 
<img width="532" height="97" alt="image" src="https://github.com/user-attachments/assets/7f531436-e988-4517-a44d-86e73c9351c6" />

Entrem a la carpeta /etc/skel i veiem que hi ha dos fitxers: accessdirector i fitxer_compartit. Aquests són els fitxers que es copien automàticament quan es crea un usuari nou.

<img width="757" height="601" alt="image" src="https://github.com/user-attachments/assets/4f634fa7-2b17-4ee7-8192-69291b0cbf52" />

Mirem què hi ha dins de /var/prova5 i veiem tant els fitxers del sistema que sempre es creen com els fitxers que venen de /etc/skel. Quan comprovem el fitxer /etc/passwd confirmem que l'usuari prova5 té el número 2000 i que el seu directori personal està ubicat a /var/prova5 en lloc de /home/prova5.

<img width="894" height="292" alt="image" src="https://github.com/user-attachments/assets/3f5efc90-c291-474d-8a64-e60ee67d9ee6" />

Mirem la informació de l'usuari prova6 al fitxer /etc/shadow i veiem que té una contrasenya configurada amb número 1120399 i algunes opcions de caducitat. Després consultem el fitxer /etc/passwd per veure la seva configuració completa on observem que prova6 té l'UID 2001 i GID 2001, el seu directori personal està a /home/prova6 i utilitza bash com a shell.

<img width="433" height="74" alt="image" src="https://github.com/user-attachments/assets/cdefda08-cce3-4e92-83de-17e56fcb3039" />

Obrim el fitxer .profile amb l'editor nano, aquest fitxer s'executa quan un usuari inicia sessió al sistema. Veiem que conté comentaris explicatius sobre la seva funció i una línia que estableix la variable PWD amb el valor "/var". El fitxer també menciona la configuració de la màscara per permisos per defecte.

<img width="682" height="207" alt="image" src="https://github.com/user-attachments/assets/bfc68ace-8d75-4a4c-baab-414efefc902f" />

Obrim el fitxer .bash_logout que s'executa quan l'usuari tanca la sessió. Conté un script que neteja la pantalla de la consola per augmentar la privadesa quan es surt del sistema, però només si és una consola local. També hi ha una línia que sembla eliminar contingut d'una carpeta d'imatges.

<img width="673" height="186" alt="image" src="https://github.com/user-attachments/assets/b97d9245-e924-4e66-8c2a-f039ef3d5bc7" />

Llistem el contingut del directori de l'usuari prova10 amb gran detall. Veiem tots els fitxers i carpetes típics d'un usuari de Linux incloent els fitxers de configuració ocults que comencen amb punt. Hi ha carpetes com Desktop, Documents, Downloads i fitxers de configuració de bash com .bashrc i .profile. També observem un fitxer anomenat filter_compartit i diverses carpetes de configuració del sistema.
<img width="522" height="356" alt="image" src="https://github.com/user-attachments/assets/bad6eea3-b691-4acf-93bc-8bdb53ddaf98" />


### Creació d'usuaris i configuració.
2.# Còpies de seguretat i automatització de tasques

4.# Gestió de procesos
