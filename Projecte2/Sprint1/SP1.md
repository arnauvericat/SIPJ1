# GUIA PRÀCTICA - Instal·lació i configuració de Windows

---

## Fase 1 - Instal·lació del sistema operatiu

- Pas 1 - Crear màquina virtual amb VirtualBox
  <img width="54" height="69" alt="image" src="https://github.com/user-attachments/assets/dfd1c667-7fc1-4a11-981d-289c533ae491" />

- Pas 2 - Assignar recursos (RAM mínim 4 GB, disc mínim 40 GB)
<img width="656" height="86" alt="image" src="https://github.com/user-attachments/assets/ebd98e4c-3e0f-4211-b404-fa2ba6d47df7" />
<img width="194" height="56" alt="image" src="https://github.com/user-attachments/assets/57b6fed8-3f98-4a82-8466-39b2a96b1978" />

- Pas 3 - Carregar ISO de Windows 10 o Windows 11
  <img width="240" height="33" alt="image" src="https://github.com/user-attachments/assets/e1c172eb-6e2e-4bb0-8625-c2b4e3af940f" />
- Pas 4 - Instal·lar el sistema (idioma, usuari, contrasenya)
<img width="425" height="307" alt="image" src="https://github.com/user-attachments/assets/77bc8e55-23b9-4a26-88ef-996dc448efcb" />
- Pas 5 - Comprovar que arrenca correctament
<img width="1025" height="769" alt="image" src="https://github.com/user-attachments/assets/82c6ff66-7310-4420-bde0-1347cba2f276" />


---

## Fase 2 - Punts de restauració

- Pas 6 - Cercar "Crear un punt de restauració"
  <img width="317" height="90" alt="image" src="https://github.com/user-attachments/assets/5af40174-d4e7-4e42-bddb-c664f53b69a0" />

- Pas 7 - Activar protecció del sistema al disc C
<img width="358" height="118" alt="image" src="https://github.com/user-attachments/assets/a761b493-9a18-4fb7-8471-210cb520db68" />

- Pas 8 - Crear un punt manual
  <img width="138" height="46" alt="image" src="https://github.com/user-attachments/assets/2b3a473f-2473-426f-925c-42af2bfb0ca6" />

- Pas 9 - Fer un canvi (instal·lar app o configuració)
- <img width="165" height="344" alt="image" src="https://github.com/user-attachments/assets/e22febef-a2c9-4d99-b0d9-fd8e2408eed8" />

  
- Pas 10 - Restaurar i comprovar  
<img width="395" height="50" alt="image" src="https://github.com/user-attachments/assets/f2d0be09-d8ce-4c1e-bc40-28872f654f61" />
<img width="292" height="94" alt="image" src="https://github.com/user-attachments/assets/b10ee1cd-ddd3-4f1d-855a-5d414231ebf5" />

---

## Fase 3 - Llicències de Windows

- Pas 11 - Obrir Configuració → Sistema → Activació  
- Pas 12 - Veure si Windows està activat  
- Pas 13 - Executar al cmd: slmgr /xpr  
- Pas 14 - Esbrinar tipus de llicència de Windows i explicar-la breument  
- Pas 15 - Consultar preu aproximat d'una llicència Windows  

---

## Fase 4 - Gestor d'arrencada

- Pas 16 - Obrir Command Prompt com administrador  
- Pas 17 - Executar bcdedit  
- Pas 18 - Identificar Boot Manager i Boot Loader  
- Pas 19 - Interpretar les dades principals  

### Pas 20 - Preguntes

- Quin sistema s'està arrencant  
- A quin disc o partició està instal·lat  
- Quant temps espera abans d'arrencar  
- Quin fitxer inicia Windows  

### Pas 21 - Explicació

- Qui decideix l'arrencada (Boot Manager)  
- Qui carrega el sistema (Boot Loader)  

---

## Fase 5 - Xarxa bàsica

- Pas 22 - Obrir configuració de xarxa  
- Pas 23 - Consultar IP amb ipconfig  
- Pas 24 - Configurar IP dinàmica (DHCP)  
- Pas 25 - Configurar IP fixa (manual)  
- Pas 26 - Comprovar connexió amb ping google.com  

---

## Fase 6 - Comandes generals

- Pas 27 - Obrir PowerShell  
- Pas 28 - Diferenciar cmd i PowerShell  
- Pas 29 - Provar comandes bàsiques (dir, cd, mkdir, echo, del)  
- Pas 30 - Provar comandes del sistema (tasklist, taskkill, systeminfo, hostname, whoami)  
- Pas 31 - Provar comandes de xarxa (ipconfig, ping, netstat)  
- Pas 32 - Provar comandes addicionals (tree, cls, help, shutdown)  

### Pas 33 - Què mostren

- tasklist  
- ipconfig  
- systeminfo  

---

## Fase 7 - Instal·lació d'aplicacions

- Pas 34 - Descarregar un programa (Chrome o VS Code)  
- Pas 35 - Instal·lar-lo  
- Pas 36 - Obrir-lo i comprovar funcionament  
- Pas 37 - Instal·lar una app des de Microsoft Store  
- Pas 38 - Obrir-la i comprovar funcionament  
- Pas 39 - Desinstal·lar una aplicació  
- Pas 40 - Comprovar que ja no apareix  
