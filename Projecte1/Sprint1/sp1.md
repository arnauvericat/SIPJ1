# Sprint 1: Avaluació, Instal·lació i Configuració de Xarxes i Sistemes Operatius

---

### Llicenciament

#### Llicència de GNU Linux

La llicència GPL (General Public License) és una llicència de programari lliure creada per garantir que els programes informàtics siguin sempre lliures, és a dir, que els usuaris tinguin la llibertat d’utilitzar-los, estudiar-ne el codi font, modificar-los i redistribuir-los, tant en la seva forma original com amb les modificacions que facin. L’objectiu de la GPL no és només permetre la còpia i distribució, sinó assegurar que qualsevol obra derivada d’un programa sota aquesta llicència continuï mantenint les mateixes llibertats, a través del principi del copyleft, que impedeix que el programari lliure es converteixi en propietari. Aquesta llicència va ser creada dins del marc del Projecte GNU, i el seu principal impulsor va ser Richard Stallman, programador i activista del programari lliure, qui va fundar la Free Software Foundation per defensar i promoure la filosofia del programari lliure. Stallman va redactar la GPL per protegir legalment els drets dels usuaris i assegurar que el coneixement i les eines informàtiques poguessin ser compartides i millorades per tothom, de manera que la llibertat del programari fos permanent.

![image](https://github.com/user-attachments/assets/048b4f58-04c3-426f-8e5a-52dd8ccbe14d)

## Virtualització i instal·lació del SO Ubuntu

Dins de la maquina ja creada hem de ficar mes opcions per a crear nosaltes les particions que volem fer.

![image](https://github.com/user-attachments/assets/18d201f2-db0b-4d24-a5ea-73ac23f8e7ec)

Dins del particionador clicarem damunt del nostre disc i crearem una partico.

![image](https://github.com/user-attachments/assets/f36625f2-7a2c-4307-924a-184519343596)

En aquest cas serà una de 40Gb per a ficar el nostre ubuntu i com el disc es de 80Gb tindrem lloc per a ficar el nostre Windows 10. Aquesta particio la ficarem com a primaria i el punt de muntatge a la nostra arrel que es la barra invertida.

![image](https://github.com/user-attachments/assets/45b42f07-07f4-444f-9798-8613771f7d47)

Una vegada creada, farem una altra particio per a ficar la efi i ficarem a quina particio volem instal·lar el nostre sistema operatiu que en aquest cas es /dev/sda1.

![image](https://github.com/user-attachments/assets/0118bea7-0982-47aa-b47b-d036d394e41f)

## Instal·lacions duals i Gestors d'arrencada

Una vegada instal·lat un sistema operatiu anirem al nostre virtual box, clicarem a parametres de la nostra maquina i anirem a emmagatzematge allí ficarem la nostra ISO del Windows 10 com a disc òptic.

![image](https://github.com/user-attachments/assets/8ef5dbba-b0e4-4f3c-b443-4a22804a105b)

Després anirem a sistema i activarem la EFI per a poder entrar i der boot amb el disc optic.

![image](https://github.com/user-attachments/assets/f2c7e1f6-127f-4dc4-9002-6cae1f41ca1b)

Ara iniciarem la maquina i clicarem esc simultaniament, això ens farà entrar a la bios i allí anirem al boot manager i iniciarem alb la nostra CD-ROM que es el disc òptic Windows.

![image](https://github.com/user-attachments/assets/ba0b9d92-67da-4aa0-995a-41ee22a29d05)

Dins de l'instal·lador anirem configurant fins a l'apartat de les instal·lacions on ficarem "Instal·lación personalizada" allí ens portara a les taules de particions que tenim, on veurem el nostre Ubuntu, una partició buida i un altre disc que serà per a la dels punts de restauració. En el nostre cas la ficarem al "Drive 0 Partition 2" que es la nostra partició buida.

![image](https://github.com/user-attachments/assets/323f719e-17b8-4b3a-93c0-2784e2abe9be)

Una vegada fet això ja començarà la instal·lació.

![image](https://github.com/user-attachments/assets/2e8ada4e-9db7-4297-a9e5-f52381a8d96c)

Quan ja tinguessem instal·lat el nostre Windows anirem a la nostra maquina virtual i treurem el disc optic de Windows i afegirem un altre que es diu super_grub2 el qual ens ajudarà a iniciar el nostre ubuntu ja que la instal·lació de windows s'ha carregar el gestor d'arrancada i ja no podem iniciar amb ubuntu.

![image](https://github.com/user-attachments/assets/0b1ff183-4b7c-4913-8f89-6383322482ad)

Com hem fet avans entrem a la nostra CD-ROM ara del super_grub2.

![image](https://github.com/user-attachments/assets/2340efe2-a2f2-4f3c-8bf1-8012a314b35b)

Dins de la rom anirem a **"Detect and show boot methods"** i buscarem el nostre ubuntu. 

![image](https://github.com/user-attachments/assets/92f16c1d-a8c9-463a-9f83-61968e5b69b9)

<!-- Las siguientes imágenes se mantienen en el mismo formato -->
![image](https://github.com/user-attachments/assets/f7124db8-5cb0-43af-b5a9-d657344815ec)
![image](https://github.com/user-attachments/assets/535767ad-4359-4c5a-8ea8-011cbe51f43e)
![image](https://github.com/user-attachments/assets/29738e40-ba0b-488f-a16e-286788a95e58)

## Particions i punts de restauració

Per a crear instantanies dintre dels nostres sistemes operatius el primer que haurem de fer es crear un disc nou sol per a ficar les nostres instantanies, si sol tenim un disc podem crear una partició i afegir-les allí. Amb un disc de 25 GB en aquest cas ens serà suficient.

![image](https://github.com/user-attachments/assets/c9631aed-6507-480d-8405-ab65f516b9ce)

<!-- Resto de imágenes en el mismo estilo... -->

## Configuració basica de la xarxa
![image](https://github.com/user-attachments/assets/10d472bc-c3af-44a2-a3e3-454eeabb5e60)
![image](https://github.com/user-attachments/assets/c1df19fa-ca38-4962-a3ec-33bb9b93aa22)
![image](https://github.com/user-attachments/assets/bf993c24-a150-426b-a276-3f4264d27143)
![image](https://github.com/user-attachments/assets/6306fcfc-1fef-4156-9466-fc3b8be76e97)
![image](https://github.com/user-attachments/assets/1145e954-775a-403f-befa-a95e34cd3901)
![image](https://github.com/user-attachments/assets/9f170759-74a6-4aba-87c5-36d7efe3bc45)
![image](https://github.com/user-attachments/assets/f25c694f-bfc3-4d34-bb73-c7526cf4b4a4)

## Comandes generals i instal·lació d'aplicacions
![image](https://github.com/user-attachments/assets/6be7a761-f05c-4118-983f-205279778d4c)
