

---

layout: default
title: "Sprint 1: Avaluació, Instal·lació i Configuració de Xarxes i Sistemes Operatius"

---

## Virtualització i instal·lació del SO Ubuntu
### Llicenciament

#### Llicència de GNU Linux

La llicència GPL (General Public License) és una llicència de programari lliure creada per garantir que els programes informàtics siguin sempre lliures, és a dir, que els usuaris tinguin la llibertat d’utilitzar-los, estudiar-ne el codi font, modificar-los i redistribuir-los, tant en la seva forma original com amb les modificacions que facin. L’objectiu de la GPL no és només permetre la còpia i distribució, sinó assegurar que qualsevol obra derivada d’un programa sota aquesta llicència continuï mantenint les mateixes llibertats, a través del principi del copyleft, que impedeix que el programari lliure es converteixi en propietari. Aquesta llicència va ser creada dins del marc del Projecte GNU, i el seu principal impulsor va ser Richard Stallman, programador i activista del programari lliure, qui va fundar la Free Software Foundation per defensar i promoure la filosofia del programari lliure. Stallman va redactar la GPL per protegir legalment els drets dels usuaris i assegurar que el coneixement i les eines informàtiques poguessin ser compartides i millorades per tothom, de manera que la llibertat del programari fos permanent.


## Instal·lacions duals i Gestors d'arrencada
<img width="634" height="327" alt="image" src="https://github.com/user-attachments/assets/ba0b9d92-67da-4aa0-995a-41ee22a29d05" />

<img width="265" height="37" alt="image" src="https://github.com/user-attachments/assets/a95f68f2-032e-4a34-a3b0-4d9750ce1aca" />

<img width="641" height="478" alt="image" src="https://github.com/user-attachments/assets/323f719e-17b8-4b3a-93c0-2784e2abe9be" />

<img width="641" height="478" alt="image" src="https://github.com/user-attachments/assets/2e8ada4e-9db7-4297-a9e5-f52381a8d96c" />



## Particions i punts de restauració
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

## Instantànies

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
