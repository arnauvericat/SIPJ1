# Sprint 1: Avaluació, Instal·lació i Configuració de Xarxes i Sistemes Operatius

---

### Llicenciament

#### Llicència de GNU Linux

La llicència GPL (General Public License) és una llicència de programari lliure creada per garantir que els programes informàtics siguin sempre lliures, és a dir, que els usuaris tinguin la llibertat d’utilitzar-los, estudiar-ne el codi font, modificar-los i redistribuir-los, tant en la seva forma original com amb les modificacions que facin. L’objectiu de la GPL no és només permetre la còpia i distribució, sinó assegurar que qualsevol obra derivada d’un programa sota aquesta llicència continuï mantenint les mateixes llibertats, a través del principi del copyleft, que impedeix que el programari lliure es converteixi en propietari. Aquesta llicència va ser creada dins del marc del Projecte GNU, i el seu principal impulsor va ser Richard Stallman, programador i activista del programari lliure, qui va fundar la Free Software Foundation per defensar i promoure la filosofia del programari lliure. Stallman va redactar la GPL per protegir legalment els drets dels usuaris i assegurar que el coneixement i les eines informàtiques poguessin ser compartides i millorades per tothom, de manera que la llibertat del programari fos permanent.

<img width="319" height="158" alt="image" src="https://github.com/user-attachments/assets/048b4f58-04c3-426f-8e5a-52dd8ccbe14d" />

## Virtualització i instal·lació del SO Ubuntu

Dins de la maquina ja creada hem de ficar mes opcions per a crear nosaltes les particions que volem fer. <br>
<img width="872" height="703" alt="image" src="https://github.com/user-attachments/assets/18d201f2-db0b-4d24-a5ea-73ac23f8e7ec" /> <br>

Dins del particionador clicarem damunt del nostre disc i crearem una partico.

<img width="847" height="635" alt="image" src="https://github.com/user-attachments/assets/f36625f2-7a2c-4307-924a-184519343596" />

En aquest cas serà una de 40Gb per a ficar el nostre ubuntu i com el disc es de 80Gb tindrem lloc per a ficar el nostre Windows 10.
Aquesta particio la ficarem com a primaria i el punt de muntatge a la nostra arrel que es la barra invertida.

<img width="540" height="320" alt="image" src="https://github.com/user-attachments/assets/45b42f07-07f4-444f-9798-8613771f7d47" />

Una vegada creada, farem una altra particio per a ficar la efi i ficarem a quina particio volem instal·lar el nostre sistema operatiu que en aquest cas es /dev/sda1.
<img width="808" height="134" alt="image" src="https://github.com/user-attachments/assets/0118bea7-0982-47aa-b47b-d036d394e41f" />


## Instal·lacions duals i Gestors d'arrencada

Una vegada instal·lat un sistema operatiu anirem al nostre virtual box, clicarem a parametres de la nostra maquina i anirem a emmagatzematge allí ficarem la nostra ISO del Windows 10 com a disc òptic.

<img width="267" height="135" alt="image" src="https://github.com/user-attachments/assets/8ef5dbba-b0e4-4f3c-b443-4a22804a105b" />

Després anirem a sistema i activarem la EFI per a poder entrar i der boot amb el disc optic.

<img width="240" height="36" alt="image" src="https://github.com/user-attachments/assets/f2c7e1f6-127f-4dc4-9002-6cae1f41ca1b" /> <br>

Ara iniciarem la maquina i clicarem esc simultaniament, això ens farà entrar a la bios i allí anirem al boot manager i iniciarem alb la nostra CD-ROM que es el disc òptic Windows.


<img width="634" height="327" alt="image" src="https://github.com/user-attachments/assets/ba0b9d92-67da-4aa0-995a-41ee22a29d05" /> <br>

Dins de l'instal·lador anirem configurant fins a l'apartat de les instal·lacions on ficarem "Instal·lación personalizada" allí ens portara a les taules de particions que tenim, on veurem el nostre Ubuntu
una partició buida i un altre disc que serà per a la dels punts de restauració. En el nostre cas la ficarem al "Drive 0 Partition 2" que es la nostra partició buida.

<img width="641" height="478" alt="image" src="https://github.com/user-attachments/assets/323f719e-17b8-4b3a-93c0-2784e2abe9be" />

Una vegada fet això ja començarà la instal·lació.

<img width="641" height="478" alt="image" src="https://github.com/user-attachments/assets/2e8ada4e-9db7-4297-a9e5-f52381a8d96c" />

Quan ja tinguessem instal·lat el nostre Windows anirem a la nostra maquina virtual i treurem el disc optic de Windows i afegirem un altre que es diu super_grub2 el qual ens ajudarà a iniciar el nostre ubuntu ja que la instal·lació de windows s'ha carregar el gestor d'arrancada i ja no podem iniciar amb ubuntu.

<img width="247" height="53" alt="image" src="https://github.com/user-attachments/assets/0b1ff183-4b7c-4913-8f89-6383322482ad" />

Com hem fet avans entrem a la nostra CD-ROM ara del super_grub2.

<img width="597" height="270" alt="image" src="https://github.com/user-attachments/assets/2340efe2-a2f2-4f3c-8bf1-8012a314b35b" />

Dins de la rom anirem a **"Detect and show boot methods"** i buscarem el nostre ubuntu. 
<img width="596" height="265" alt="image" src="https://github.com/user-attachments/assets/92f16c1d-a8c9-463a-9f83-61968e5b69b9" />



<img width="618" height="79" alt="image" src="https://github.com/user-attachments/assets/f7124db8-5cb0-43af-b5a9-d657344815ec" />

<img width="698" height="251" alt="image" src="https://github.com/user-attachments/assets/535767ad-4359-4c5a-8ea8-011cbe51f43e" />

<img width="689" height="282" alt="image" src="https://github.com/user-attachments/assets/29738e40-ba0b-488f-a16e-286788a95e58" />



## Particions i punts de restauració

Per a crear instantanies dintre dels nostres sistemes operatius el primer que haurem de fer es crear un disc nou sol per a ficar les nostres instantanies, si sol tenim un disc podem crear una partició i afegir-les allí.
Amb un disc de 25 GB en aquest cas ens serà suficient.

<img width="878" height="575" alt="image" src="https://github.com/user-attachments/assets/c9631aed-6507-480d-8405-ab65f516b9ce" />

Dins del nostre ubuntu, buscarem el nostre disc nou, això ho podem fer amb la comanda sudo fdisk -l, una vegada veiguem quin es el disc que hem ficat, que en aquest cas es sdb, farem la comanda següent.

<img width="738" height="204" alt="image" src="https://github.com/user-attachments/assets/a80ac162-2b37-4693-a93d-8900f842d191" />

Amb aquesta comanda particionarem el nostre disc, en aquest cas farem servir tot el disc aixi que ficarem els 25GB que tenim de disc, això ho farem fent la comanda fdisk /dev/sdb, una vegada dins del particionador ficarem una n per a crear una "new partition", després una p per a ferla primaria i clicarem enter per a tot el següent, això utilitzarà tot l'espai del disc per defecte, una vegada creada clicarem a w per a sortir.

<img width="855" height="188" alt="image" src="https://github.com/user-attachments/assets/0f2a9819-abf8-4066-9bdf-d418eace50ad" />

<img width="791" height="227" alt="image" src="https://github.com/user-attachments/assets/1437f7a3-aa9e-4619-938d-adb37de3ceba" />

<img width="736" height="137" alt="image" src="https://github.com/user-attachments/assets/f2731f9c-c317-45b9-b574-5733ac788862" />

<img width="592" height="656" alt="image" src="https://github.com/user-attachments/assets/21a53a94-bae4-4a20-8e34-59a4ac09e8ef" />

<img width="592" height="656" alt="image" src="https://github.com/user-attachments/assets/393a90f7-df57-4567-b9ca-78603100db11" />

<img width="592" height="656" alt="image" src="https://github.com/user-attachments/assets/6f9869a2-7b0f-4143-8add-1710c76888f8" />

<img width="916" height="91" alt="image" src="https://github.com/user-attachments/assets/582ea69e-ef1f-40f7-b25f-e21942836ce9" />

<img width="754" height="248" alt="image" src="https://github.com/user-attachments/assets/09d67dd8-637b-4818-a4ab-604ef83a75e4" />

<img width="501" height="549" alt="image" src="https://github.com/user-attachments/assets/628c269a-c0d3-485f-b4ba-2984b4d38a3d" />

<img width="803" height="631" alt="image" src="https://github.com/user-attachments/assets/c87f6045-41e0-4801-8855-fe8a1f4031e4" />

<img width="954" height="797" alt="image" src="https://github.com/user-attachments/assets/0b57ce22-54b3-4153-b702-cb3489406885" />

## Configuració basica de la xarxa
<img width="582" height="445" alt="image" src="https://github.com/user-attachments/assets/10d472bc-c3af-44a2-a3e3-454eeabb5e60" />
<img width="925" height="546" alt="image" src="https://github.com/user-attachments/assets/c1df19fa-ca38-4962-a3ec-33bb9b93aa22" />
<img width="595" height="189" alt="image" src="https://github.com/user-attachments/assets/bf993c24-a150-426b-a276-3f4264d27143" />
<img width="576" height="466" alt="image" src="https://github.com/user-attachments/assets/6306fcfc-1fef-4156-9466-fc3b8be76e97" />
<img width="730" height="479" alt="image" src="https://github.com/user-attachments/assets/1145e954-775a-403f-befa-a95e34cd3901" />
<img width="728" height="308" alt="image" src="https://github.com/user-attachments/assets/9f170759-74a6-4aba-87c5-36d7efe3bc45" />
<img width="823" height="118" alt="image" src="https://github.com/user-attachments/assets/f25c694f-bfc3-4d34-bb73-c7526cf4b4a4" />



## Comandes generals i instal·lació d'aplicacions
<img width="724" height="148" alt="image" src="https://github.com/user-attachments/assets/6be7a761-f05c-4118-983f-205279778d4c" />
