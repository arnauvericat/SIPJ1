---
title: "Sprint 1: Avaluació, Instal·lació i Configuració de Xarxes i Sistemes Operatius"
---

#### Llicència de GNU Linux

La llicència GPL (General Public License) és una llicència de programari lliure creada per garantir que els programes informàtics siguin sempre lliures, és a dir, que els usuaris tinguin la llibertat d’utilitzar-los, estudiar-ne el codi font, modificar-los i redistribuir-los, tant en la seva forma original com amb les modificacions que facin. L’objectiu de la GPL no és només permetre la còpia i distribució, sinó assegurar que qualsevol obra derivada d’un programa sota aquesta llicència continuï mantenint les mateixes llibertats, a través del principi del copyleft, que impedeix que el programari lliure es converteixi en propietari. Aquesta llicència va ser creada dins del marc del Projecte GNU, i el seu principal impulsor va ser Richard Stallman, programador i activista del programari lliure, qui va fundar la Free Software Foundation per defensar i promoure la filosofia del programari lliure. Stallman va redactar la GPL per protegir legalment els drets dels usuaris i assegurar que el coneixement i les eines informàtiques poguessin ser compartides i millorades per tothom, de manera que la llibertat del programari fos permanent.

<img src="https://github.com/user-attachments/assets/048b4f58-04c3-426f-8e5a-52dd8ccbe14d" style="display:block; margin-top:10px;" alt="imatge descriptiva">

## Virtualització i instal·lació del SO Ubuntu

Dins de la maquina ja creada hem de ficar mes opcions per a crear nosaltes les particions que volem fer.

<img src="https://github.com/user-attachments/assets/18d201f2-db0b-4d24-a5ea-73ac23f8e7ec" style="display:block; margin-top:10px;" alt="imatge">

Dins del particionador clicarem damunt del nostre disc i crearem una partico.

<img src="https://github.com/user-attachments/assets/f36625f2-7a2c-4307-924a-184519343596" style="display:block; margin-top:10px;" alt="imatge">

En aquest cas serà una de 40Gb per a ficar el nostre ubuntu i com el disc es de 80Gb tindrem lloc per a ficar el nostre Windows 10. Aquesta particio la ficarem com a primaria i el punt de muntatge a la nostra arrel que es la barra invertida.

<img src="https://github.com/user-attachments/assets/45b42f07-07f4-444f-9798-8613771f7d47" style="display:block; margin-top:10px;" alt="imatge">

Una vegada creada, farem una altra particio per a ficar la efi i ficarem a quina particio volem instal·lar el nostre sistema operatiu que en aquest cas es /dev/sda1.

<img src="https://github.com/user-attachments/assets/0118bea7-0982-47aa-b47b-d036d394e41f" style="display:block; margin-top:10px;" alt="imatge">

## Instal·lacions duals i Gestors d'arrencada

Una vegada instal·lat un sistema operatiu anirem al nostre virtual box, clicarem a paràmetres de la nostra màquina i anirem a emmagatzematge allí ficarem la nostra ISO del Windows 10 com a disc òptic.

<img src="https://github.com/user-attachments/assets/8ef5dbba-b0e4-4f3c-b443-4a22804a105b" style="display:block; margin-top:10px;" alt="imatge">

Després anirem a sistema i activarem la EFI per a poder entrar i fer boot amb el disc òptic.

<img src="https://github.com/user-attachments/assets/f2c7e1f6-127f-4dc4-9002-6cae1f41ca1b" style="display:block; margin-top:10px;" alt="imatge">

Ara iniciarem la màquina i clicarem ESC simultàniament, això ens farà entrar a la BIOS i allí anirem al boot manager i iniciarem amb la nostra CD-ROM que és el disc òptic de Windows.

<img src="https://github.com/user-attachments/assets/ba0b9d92-67da-4aa0-995a-41ee22a29d05" style="display:block; margin-top:10px;" alt="imatge">

Dins de l'instal·lador anirem configurant fins a l'apartat de les instal·lacions on ficarem "Instal·lación personalizada", allí ens portarà a les taules de particions que tenim, on veurem el nostre Ubuntu, una partició buida i un altre disc que serà per als punts de restauració. En el nostre cas la ficarem al "Drive 0 Partition 2" que és la nostra partició buida.

<img src="https://github.com/user-attachments/assets/323f719e-17b8-4b3a-93c0-2784e2abe9be" style="display:block; margin-top:10px;" alt="imatge">

Una vegada fet això ja començarà la instal·lació.

<img src="https://github.com/user-attachments/assets/2e8ada4e-9db7-4297-a9e5-f52381a8d96c" style="display:block; margin-top:10px;" alt="imatge">

Quan ja tinguéssim instal·lat el nostre Windows, anirem a la nostra màquina virtual i treurem el disc òptic de Windows i afegirem un altre que es diu super_grub2, el qual ens ajudarà a iniciar el nostre Ubuntu ja que la instal·lació de Windows s'ha carregat el gestor d'arrancada i ja no podem iniciar amb Ubuntu.

<img src="https://github.com/user-attachments/assets/0b1ff183-4b7c-4913-8f89-6383322482ad" style="display:block; margin-top:10px;" alt="imatge">

Com hem fet abans, entrem a la nostra CD-ROM ara del super_grub2.

<img src="https://github.com/user-attachments/assets/2340efe2-a2f2-4f3c-8bf1-8012a314b35b" style="display:block; margin-top:10px;" alt="imatge">

Dins de la ROM anirem a **"Detect and show boot methods"** i buscarem el nostre Ubuntu. 

<img src="https://github.com/user-attachments/assets/92f16c1d-a8c9-463a-9f83-61968e5b69b9" style="display:block; margin-top:10px;" alt="imatge">

Ara dins del nostre Ubuntu farem la comanda `grub-install` dins del nostre disc que és el `/dev/sdb`.

<img src="https://github.com/user-attachments/assets/f7124db8-5cb0-43af-b5a9-d657344815ec" style="display:block; margin-top:10px;" alt="imatge">

Després farem un update per a que es quedi guardat i ens dirigirem al arxiu `/etc/default/grub`.

<img src="https://github.com/user-attachments/assets/535767ad-4359-4c5a-8ea8-011cbe51f43e" style="display:block; margin-top:10px;" alt="imatge">

Aquí dins ficarem o buscarem i descomentarem la línia `GRUB_DISABLE_OS_PROBER=false` i ja podrem accedir als nostres dos sistemes. <br>

<img src="https://github.com/user-attachments/assets/29738e40-ba0b-488f-a16e-286788a95e58" style="display:block; margin-top:10px;" alt="imatge">

Es veuria tal que així.

<img src="https://github.com/user-attachments/assets/703edf6d-cdd1-4051-909d-963843430a13" style="display:block; margin-top:10px;" alt="imatge">

## Particions i punts de restauració

Per a crear instantànies dintre dels nostres sistemes operatius, el primer que haurem de fer és crear un disc nou sol per a ficar les nostres instantànies. Si només tenim un disc podem crear una partició i afegir-les allí. Amb un disc de 25 GB en aquest cas ens serà suficient.

<img src="https://github.com/user-attachments/assets/c9631aed-6507-480d-8405-ab65f516b9ce" style="display:block; margin-top:10px;" alt="imatge">

Una vegada creada entrarem al nostre ubuntu i farem la comanda següent `fdisk /dev/sdb` aquest es el disc on ficarem els nostres punts de restauració. Aquesta comanda ens permet parcicionar el disc i donar-li un format.

<img src="https://github.com/user-attachments/assets/15ff3d2a-2251-4e3f-ac1e-e44cf8113e09" style="display:block; margin-top:10px;" alt="imatge"/>

Dins del disc clicarem la **N** per a crear una `new partition`.
Després clicarem la **P** per a fer una partició `primary`. Als següents apartats farem `intro` ja que no son importants per a aquest cas.

<img src="https://github.com/user-attachments/assets/7efbf78b-05a8-477c-a8c3-880e08c7aa63" style="display:block; margin-top:10px;" alt="imatge"/>

Despres de sortir del particionador farem la comanda `mkfs.ext4 /dev/sdb1` que en aquest cas sdb1 es la nova particio del disc que ocupa els 25GB, aquesta comanda server per a crear un gestor de fitxers `mkfs` amb el format `ext4` dins del disc `/dev/sdb1`.

<img src="https://github.com/user-attachments/assets/5a7f98f9-4418-460e-beaf-86ee149fc1fb" style="display:block; margin-top:10px;" alt="imatge"/>

Ara ja estem llistos per a descarregar **Timeshift** que es el que ens servirà per a crear els nostres punts de restauració. Això ho podem fer amb la comanda `sudo apt install timeshift`.

<img src="https://github.com/user-attachments/assets/0ae94e1d-248b-4195-84eb-273907103bec" style="display:block; margin-top:10px;" alt="imatge"/>



<img src="https://github.com/user-attachments/assets/538e6318-7462-48f9-a868-2cf8757045fe" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/44dfc67e-5560-4e50-a445-4fb9f3611d67" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/a64e300d-3e33-41c6-a4e7-f0b0f6509e10" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/5cc3f479-4e55-4fcf-9297-a0e99224be33" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/fcf485fd-5350-4f59-af89-51c68ae9bf6d" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/796a21a8-4749-4b6b-9c3a-999bfe601c59" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/dd648677-053e-4282-8653-d93dad3677f3" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/8c6bf066-4767-4e44-bc88-5e9864719cf5" style="display:block; margin-top:10px;" alt="imatge">

## Configuració bàsica de la xarxa

<img src="https://github.com/user-attachments/assets/10d472bc-c3af-44a2-a3e3-454eeabb5e60" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/c1df19fa-ca38-4962-a3ec-33bb9b93aa22" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/bf993c24-a150-426b-a276-3f4264d27143" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/6306fcfc-1fef-4156-9466-fc3b8be76e97" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/1145e954-775a-403f-befa-a95e34cd3901" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/9f170759-74a6-4aba-87c5-36d7efe3bc45" style="display:block; margin-top:10px;" alt="imatge">

<img src="https://github.com/user-attachments/assets/f25c694f-bfc3-4d34-bb73-c7526cf4b4a4" style="display:block; margin-top:10px;" alt="imatge">

## Comandes generals i instal·lació d'aplicacions

<img src="https://github.com/user-attachments/assets/6be7a761-f05c-4118-983f-205279778d4c" style="display:block; margin-top:10px;" alt="imatge">
