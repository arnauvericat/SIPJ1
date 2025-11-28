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

<img width="556" height="78" alt="image" src="https://github.com/user-attachments/assets/a96e5301-0ca9-4bd6-a567-26a96e28914e" />

<img width="613" height="95" alt="image" src="https://github.com/user-attachments/assets/2147a87a-b62f-420e-a57c-0f5b2511d91f" />

<img width="374" height="62" alt="image" src="https://github.com/user-attachments/assets/935ee461-6458-46a7-b170-9b8d7d2f7b5d" />

<img width="612" height="144" alt="image" src="https://github.com/user-attachments/assets/9bd4a661-80de-4656-b5ef-b28cf68221a6" />

<img width="725" height="265" alt="image" src="https://github.com/user-attachments/assets/79b65e7e-4ab9-4779-b553-1267767aa103" />

<img width="294" height="46" alt="image" src="https://github.com/user-attachments/assets/9a18a701-5bec-4696-9586-6c70614acb8d" />

3.# Gestió d'usuaris, grups i permisos

<img width="1201" height="698" alt="image" src="https://github.com/user-attachments/assets/57848529-7400-455e-b369-a96a3338b95d" />
<img width="1205" height="713" alt="image" src="https://github.com/user-attachments/assets/ce434aac-c401-481d-92ee-55bd4997de0a" />
<img width="1205" height="713" alt="image" src="https://github.com/user-attachments/assets/395232d9-f102-4f1b-aa94-dab4fb55cb66" />
<img width="1205" height="713" alt="image" src="https://github.com/user-attachments/assets/c1c979c1-f723-4321-b536-19ef3a17c191" />
<img width="537" height="381" alt="image" src="https://github.com/user-attachments/assets/0f830fa8-e299-45b3-9509-e2991572f41d" />
<img width="713" height="313" alt="image" src="https://github.com/user-attachments/assets/efc12a8a-3819-4180-8686-0527aabd6d09" />
<img width="397" height="39" alt="image" src="https://github.com/user-attachments/assets/feb37c0f-3e3b-4aa9-88a0-00c1671ce389" />
<img width="731" height="44" alt="image" src="https://github.com/user-attachments/assets/de60d0d6-044f-4862-a09f-dba1a3fb5d37" />
<img width="511" height="41" alt="image" src="https://github.com/user-attachments/assets/15c9c37f-5bad-4ff9-9ee9-35e33abfc98b" />
<img width="511" height="41" alt="image" src="https://github.com/user-attachments/assets/585a3b5c-8ceb-4dc3-b3fa-d3c615ec8b99" />
<img width="526" height="94" alt="image" src="https://github.com/user-attachments/assets/5e0c84e2-1cd9-4326-a5db-44030b3c170b" />
<img width="444" height="41" alt="image" src="https://github.com/user-attachments/assets/280b2fed-fe76-497f-9eea-fc5dc89d11b8" />
<img width="481" height="110" alt="image" src="https://github.com/user-attachments/assets/9e0c5ec0-38ad-4b1b-b218-3dc60e9a15b1" />
<img width="734" height="106" alt="image" src="https://github.com/user-attachments/assets/ff534e70-2dae-4ba1-b0cd-b8db51ebcc6b" />


<img width="520" height="151" alt="image" src="https://github.com/user-attachments/assets/58318732-0275-4208-87c8-94ddce89e015" />
<img width="536" height="77" alt="image" src="https://github.com/user-attachments/assets/62b11c66-b800-4462-bcf6-2c534e2ba2a1" />
<img width="907" height="97" alt="image" src="https://github.com/user-attachments/assets/eb5175fd-8175-440b-bb1d-894b12d06cd3" />
<img width="902" height="65" alt="image" src="https://github.com/user-attachments/assets/6b9205ff-094b-45d8-8185-be1e19476af9" />
<img width="421" height="216" alt="image" src="https://github.com/user-attachments/assets/c68e61a2-bd1b-46e9-b5a6-fa50ba6193da" />
<img width="435" height="151" alt="image" src="https://github.com/user-attachments/assets/7919c607-dd30-436c-98d9-16e7b2a7ea3a" />
<img width="434" height="46" alt="image" src="https://github.com/user-attachments/assets/5c1e7d97-b114-4c33-9ac4-2a02689cbe2f" />
<img width="434" height="23" alt="image" src="https://github.com/user-attachments/assets/6db9c054-a8b4-4b3a-85aa-4078bc3f66c1" />
<img width="428" height="43" alt="image" src="https://github.com/user-attachments/assets/4dd084f7-c4f8-40a2-9a95-3ecf6bf0a214" />
<img width="302" height="39" alt="image" src="https://github.com/user-attachments/assets/e8d7efa7-bbdb-4470-8df5-5eae92ef5230" />
<img width="532" height="97" alt="image" src="https://github.com/user-attachments/assets/7f531436-e988-4517-a44d-86e73c9351c6" />


<img width="757" height="601" alt="image" src="https://github.com/user-attachments/assets/4f634fa7-2b17-4ee7-8192-69291b0cbf52" />
<img width="894" height="292" alt="image" src="https://github.com/user-attachments/assets/3f5efc90-c291-474d-8a64-e60ee67d9ee6" />
<img width="433" height="74" alt="image" src="https://github.com/user-attachments/assets/cdefda08-cce3-4e92-83de-17e56fcb3039" />

<img width="682" height="207" alt="image" src="https://github.com/user-attachments/assets/bfc68ace-8d75-4a4c-baab-414efefc902f" />
<img width="673" height="186" alt="image" src="https://github.com/user-attachments/assets/b97d9245-e924-4e66-8c2a-f039ef3d5bc7" />
<img width="522" height="356" alt="image" src="https://github.com/user-attachments/assets/bad6eea3-b691-4acf-93bc-8bdb53ddaf98" />


### Creació d'usuaris i configuració.
2.# Còpies de seguretat i automatització de tasques

4.# Gestió de procesos
