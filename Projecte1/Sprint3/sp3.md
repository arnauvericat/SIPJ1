# SPRINT 3: GESTIÓ DE DOMINIS I ACCESSOS  

INSTAL·LACIÓ DOMINI LDAP I UNIR CLIENT AL DOMINI

El primer que hem de fer per a instal·lar el domini ldap es ficar una ip fixa per al nostre servidor, ja que els nostres equips amb els usuaris han de connectar-se i es millor una ip fixa per a no tindre que canviar-ho tot el rato.

<img width="580" height="473" alt="image" src="https://github.com/user-attachments/assets/4d1799b8-099c-4589-b809-963d72cc57b5" />


<img width="488" height="44" alt="image" src="https://github.com/user-attachments/assets/e3839fc7-9e85-41e3-bc12-1bd5d072defa" />

<img width="487" height="96" alt="image" src="https://github.com/user-attachments/assets/1816ed3f-ccb7-4770-b942-6704b4f39725" />

<img width="475" height="256" alt="image" src="https://github.com/user-attachments/assets/58b625dc-e170-4f61-a5b7-b3e403d06068" />

# Reconfigure-slapd

<img width="848" height="175" alt="image" src="https://github.com/user-attachments/assets/7d4ef823-64fc-4dc8-a1dc-2848ab06d7d1" />

<img width="1400" height="176" alt="image" src="https://github.com/user-attachments/assets/537b0add-0d40-4283-976f-d8a547b86415" />

<img width="778" height="177" alt="image" src="https://github.com/user-attachments/assets/eb3f5f5b-3075-4f96-8b0a-b9ca157619af" />

<img width="760" height="176" alt="image" src="https://github.com/user-attachments/assets/a9aea36d-4870-428c-bc31-57b2d77ec174" />

<img width="1069" height="195" alt="image" src="https://github.com/user-attachments/assets/841be554-5aa0-4dab-b8fa-e501d3433242" />

<img width="651" height="181" alt="image" src="https://github.com/user-attachments/assets/15b47a5f-209c-4a92-a31a-3a7a5823a0fc" />

<img width="497" height="258" alt="image" src="https://github.com/user-attachments/assets/e048ac1b-45b9-414b-b4c7-e063b3b0d7e0" />

<img width="294" height="97" alt="image" src="https://github.com/user-attachments/assets/48d91f29-cbdd-4268-9c4a-545f86bdd3a1" />

<img width="365" height="371" alt="image" src="https://github.com/user-attachments/assets/8d262b06-9e25-4dfa-b53e-495cb4f99898" />

<img width="944" height="205" alt="image" src="https://github.com/user-attachments/assets/7cbd69ac-9653-446a-aa38-5172cb1d563d" />


# Unir un client al domini ldap

<img width="725" height="27" alt="image" src="https://github.com/user-attachments/assets/db407520-0ee2-466d-b28a-3bd36fb7a723" />

<img width="853" height="279" alt="image" src="https://github.com/user-attachments/assets/9fcb9dd0-75eb-4297-9842-f636b15f639c" />

<img width="837" height="221" alt="image" src="https://github.com/user-attachments/assets/67d6d5d5-fd18-4564-a710-93044906afbe" />

<img width="837" height="221" alt="image" src="https://github.com/user-attachments/assets/e9857d05-80f5-444c-a3d2-067662bd3c3e" />

<img width="828" height="242" alt="image" src="https://github.com/user-attachments/assets/c6fd37aa-4688-45e6-8ae6-fb8aaa1bb983" />

<img width="828" height="242" alt="image" src="https://github.com/user-attachments/assets/bc8bff51-68f2-4bce-b594-f49b1aa6770e" />

<img width="553" height="229" alt="image" src="https://github.com/user-attachments/assets/b62aec64-11fc-4a7a-aea3-12f6d7ab01c0" />

<img width="800" height="298" alt="image" src="https://github.com/user-attachments/assets/11571806-caa2-40dd-b5a2-6f9fb145e1fc" />

<img width="851" height="234" alt="image" src="https://github.com/user-attachments/assets/34bae554-8fba-4b52-ba7d-2ceed8a79963" />

<img width="719" height="198" alt="image" src="https://github.com/user-attachments/assets/2e7127e0-ce5a-4df1-92d4-85320d45e0b5" />

## Nsswitch.conf

<img width="696" height="437" alt="image" src="https://github.com/user-attachments/assets/38d6594e-036d-42bc-bfb8-12828d814748" />

## pam.d/common-session

<img width="554" height="31" alt="image" src="https://github.com/user-attachments/assets/68be4064-a0ab-4ffb-bae9-b4e79272196c" />

## common-password

<img width="841" height="95" alt="image" src="https://github.com/user-attachments/assets/359502f7-ccca-47f5-ba65-89ebe728c7a8" />

## Lightdm.conf

<img width="704" height="84" alt="image" src="https://github.com/user-attachments/assets/07db0f95-0c0b-4463-a092-667d42395d81" />

# Proves
<img width="582" height="114" alt="image" src="https://github.com/user-attachments/assets/d217d225-c639-44e2-b5ba-d5d94a9b1d53" />

<img width="341" height="62" alt="image" src="https://github.com/user-attachments/assets/70eb18d2-d590-4c90-9d7c-73ba519008e5" />

### Servidor samba

Serveix per a compartir arxius, recursos, impresores, etc. Tambe te autenticació a nivell ldap.

<img width="711" height="152" alt="image" src="https://github.com/user-attachments/assets/3a02267b-0321-4930-aaac-494303d0c774" />

<img width="692" height="187" alt="image" src="https://github.com/user-attachments/assets/471bbe62-af35-4bd4-9117-233b7492a059" />

<img width="508" height="470" alt="image" src="https://github.com/user-attachments/assets/ca63b010-94a9-4eeb-b9de-a586dc54dd14" />

<img width="446" height="212" alt="image" src="https://github.com/user-attachments/assets/6d4aa067-8909-4b30-93ab-a3dc30572e97" />

<img width="446" height="212" alt="image" src="https://github.com/user-attachments/assets/1fac8386-36c0-4ece-b4bf-49d47204341d" />

<img width="881" height="660" alt="image" src="https://github.com/user-attachments/assets/2b6b91fd-aa03-4567-9fd1-7513de26760f" />

### Client samba

<img width="543" height="22" alt="image" src="https://github.com/user-attachments/assets/a8b23c6e-dafd-4619-b860-11d5a46b68c5" />

<img width="372" height="97" alt="image" src="https://github.com/user-attachments/assets/b376bbb2-8485-4b47-b710-073ce8fc6642" />

Efectivament no va

<img width="600" height="426" alt="image" src="https://github.com/user-attachments/assets/2f8b6d6b-45b3-48a5-9165-a1476bec3592" />

<img width="600" height="426" alt="image" src="https://github.com/user-attachments/assets/7d9202ab-1ea4-4ae4-ad75-7295cb5ba38f" />


### Servidor NFS

Instal·lació nfs-kernel-server

<img width="729" height="340" alt="image" src="https://github.com/user-attachments/assets/a7c544bf-6c19-41ba-afb1-b28fb2bf1811" />

<img width="728" height="203" alt="image" src="https://github.com/user-attachments/assets/a22aa9e8-1f75-4983-94cc-60b54de3886c" />

<img width="728" height="203" alt="image" src="https://github.com/user-attachments/assets/e33166b8-d82f-43ea-a699-543a5450d7e0" />

<img width="730" height="235" alt="image" src="https://github.com/user-attachments/assets/d40aa780-af20-4124-b395-56b50db750ae" />

<img width="366" height="80" alt="image" src="https://github.com/user-attachments/assets/072ce7c3-b5ca-4360-bb1f-78e81205713d" />

<img width="301" height="46" alt="image" src="https://github.com/user-attachments/assets/2e9ddc74-289d-4b52-81e0-6a7462660b25" />

<img width="364" height="256" alt="image" src="https://github.com/user-attachments/assets/a8c5dc74-2553-4b07-a1ca-cd410f430558" />

<img width="728" height="75" alt="image" src="https://github.com/user-attachments/assets/39dd9b73-7022-44f2-9b6b-e992a3a6b581" />


### Client NFS

<img width="733" height="313" alt="image" src="https://github.com/user-attachments/assets/c160abed-9fdf-40e0-96a5-8740e851e067" />

<img width="431" height="50" alt="image" src="https://github.com/user-attachments/assets/a5fb86e2-9e34-4423-b985-fce964a435d7" />
<img width="859" height="28" alt="image" src="https://github.com/user-attachments/assets/167175c5-cc5d-4b5d-aeb7-ed520d530ae2" />

<img width="225" height="25" alt="image" src="https://github.com/user-attachments/assets/7738ae26-c491-4271-96de-7df311e3be17" />

<img width="424" height="83" alt="image" src="https://github.com/user-attachments/assets/a9b0152f-6219-4f69-9301-3b566ec28282" />

<img width="403" height="113" alt="image" src="https://github.com/user-attachments/assets/a270c9e8-6d8a-48f2-969a-4b07a79a8cd7" />


<img width="872" height="41" alt="image" src="https://github.com/user-attachments/assets/78aa6299-2270-4c73-af5d-0e0997cbd15a" />



### Exercici NFS

Connectar un windows a la carpeta del server amb NFS
