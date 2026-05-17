# Guia de Configuració de Sistemes: Discs, Quotes, Scripts i ACLs

Aquest document detalla el procés de configuració d'un entorn Windows per a la gestió d'usuaris, optimització de recursos i control de fitxers.

## 🛠 Fase 1 – Preparació del sistema

* [ ] **Pas 1.** Afegir un nou disc virtual a la màquina virtual.
  <img width="500" height="439" alt="image" src="https://github.com/user-attachments/assets/e8f5cd6f-d831-40d8-8e82-fa93b5388ebd" />

* [ ] **Pas 2.** Iniciar Windows i obrir **Gestió de discs**.
<img width="750" height="594" alt="shot_1778843455" src="https://github.com/user-attachments/assets/60f714c5-3dcd-4f12-b155-88c72e1ce843" />

* [ ] **Pas 3.** Inicialitzar el disc i crear dues particions:
* `Dades`: Format NTFS.
* `Portable`: Format FAT32.
<img width="544" height="112" alt="shot_1778843602" src="https://github.com/user-attachments/assets/e42e2c7b-49a0-4612-aee6-ea1ab78be5ac" />


* [ ] **Pas 4.** Assignar lletres d'unitat i verificar la configuració mitjançant la consola amb l'ordre `diskpart`.

<img width="562" height="46" alt="shot_1778843788" src="https://github.com/user-attachments/assets/0d496bd8-cf85-4c99-b4b0-d34935420526" />

## 👥 Fase 2 – Quotes i usuaris

* [ ] **Pas 5.** Activar les **quotes de disc** a la partició `Dades` (NTFS).
* [ ] **Pas 6.** Establir un límit de **300 MB** per usuari amb notificació d’advertència.
<img width="361" height="497" alt="shot_1778843999" src="https://github.com/user-attachments/assets/f81b85df-ce05-4490-928d-f9ff078a6b84" />

* [ ] **Pas 7.** Crear dos usuaris locals: `alumne1` i `alumne2`.
<img width="466" height="128" alt="shot_1778844108" src="https://github.com/user-attachments/assets/5fa7906e-db20-43f1-a662-be11180bf852" />
<img width="422" height="122" alt="shot_1778844127" src="https://github.com/user-attachments/assets/328b5877-011b-4628-9f36-0dabee7633cb" />

* [ ] **Pas 8.** Crear un grup anomenat `Limitats` i afegir-hi ambdós usuaris.
<img width="404" height="44" alt="shot_1778844165" src="https://github.com/user-attachments/assets/8584a6ae-608f-490a-bcb2-39c4c245958c" />
<img width="498" height="73" alt="shot_1778859749" src="https://github.com/user-attachments/assets/dae73155-a5d9-4284-895b-85495c54064b" />

* [ ] **Pas 9.** Provar la còpia de fitxers a `Dades` fins a superar el límit per verificar el bloqueig de la quota.
<img width="265" height="76" alt="shot_1778859699" src="https://github.com/user-attachments/assets/7a9ae3ff-3f22-4985-8bda-736bcd7934a7" />
<img width="498" height="73" alt="shot_1778859749" src="https://github.com/user-attachments/assets/0200a090-1795-4902-a5c3-67e4dd6649e0" />


## 📜 Fase 3 – Script de còpia i automatització

* [ ] **Pas 10.** Afegir un tercer disc virtual i formatar-lo en NTFS com a `Backups`.
  <img width="358" height="108" alt="image" src="https://github.com/user-attachments/assets/1d3b05d1-4306-46a6-9bda-0dabc8bff9bf" />

* [ ] **Pas 11.** Crear la carpeta `CòpiesUsuaris` dins de la unitat de `Backups`.
  <img width="334" height="112" alt="image" src="https://github.com/user-attachments/assets/36d66354-6a88-4ebd-abc1-81a0983a5702" />

* [ ] **Pas 12.** Crear un script `.bat` amb el següent contingut:
<img width="573" height="154" alt="image" src="https://github.com/user-attachments/assets/c1d9c3f5-0f9b-4314-850b-97ce0bed0e33" />


* [ ] **Pas 13.** Obrir `gpedit.msc` → *Configuració d’usuari* → *Scripts* → *Inici de sessió*.
  <img width="762" height="529" alt="image" src="https://github.com/user-attachments/assets/952ce527-bc65-4d73-bd52-138ebccd7703" />

* [ ] **Pas 14.** Assignar l’script perquè s’executi automàticament en iniciar la sessió els usuaris.
<img width="385" height="200" alt="image" src="https://github.com/user-attachments/assets/8025fda8-0ec3-46be-8b10-b58c908fca10" />

## 🔍 Fase 4 – Verificació i documentació

* [ ] **Pas 15.** Iniciar sessió amb `alumne1` i realitzar les comprovacions:
* L'script s'ha executat i ha creat la còpia a `Backups`.
* La quota a `Dades` funciona correctament.
<img width="658" height="153" alt="image" src="https://github.com/user-attachments/assets/9977ce2c-a9d2-4d3f-9ddc-4ac791eff174" />
<img width="284" height="69" alt="image" src="https://github.com/user-attachments/assets/f6d5985e-c75e-49a8-b695-4c9532d360db" />



## ⚡ Fase 5 – Gestió de processos i serveis

### Pas 19. Llistar processos actius

1. Inicia sessió com `alumne1`.
2. Obre la consola (`cmd`).
3. Executa i exporta el llistat:
```cmd
tasklist > C:\Users\%USERNAME%\processos_inici.txt

```
<img width="610" height="47" alt="image" src="https://github.com/user-attachments/assets/7010a455-6735-44c0-b443-781753ecba5c" />
| Nom del procés | Memòria usada | Justificació per eliminar-lo |
<img width="635" height="33" alt="image" src="https://github.com/user-attachments/assets/ecfc9162-1870-4606-bb57-14d441bc7315" />
<img width="631" height="21" alt="image" src="https://github.com/user-attachments/assets/5ff41f4b-3eff-4d9b-bd28-9ece279c76e0" />


### Pas 20. Identificar processos prescindibles

<img width="631" height="21" alt="shot_1778861698" src="https://github.com/user-attachments/assets/2b62e91a-7ef7-437f-85ac-1ff9aadd376b" />


### Pas 21. Eliminar processos manualment

Executa per tancar processos innecessaris:
<img width="498" height="47" alt="shot_1778861811" src="https://github.com/user-attachments/assets/74597f97-34db-43c5-80ff-91190517d307" />

#### Avans
<img width="628" height="62" alt="shot_1778861857" src="https://github.com/user-attachments/assets/b38f4a2d-e0db-4ada-ba11-03d728f2f40c" />

#### Després 
<img width="647" height="39" alt="shot_1778861873" src="https://github.com/user-attachments/assets/aeca6d19-d8f9-4e73-aa63-88e99c48d5b2" />


### Pas 22. Automatització

Modifica l'script d'inici de sessió afegint:
<img width="310" height="112" alt="shot_1778861950" src="https://github.com/user-attachments/assets/1f41c2d8-d6d4-4c01-9c56-95e7e9a327c0" />


### Pas 23. Documentació de rendiment

* Explicar l'efecte de matar processos crítics com `explorer.exe` (es perd la interfície gràfica).

> Quan es mata un procés crític com explorer.exe a Microsoft Windows Explorer, el sistema operatiu continua funcionant, però es perd la interfície gràfica principal de l’usuari. Això significa que > desapareixen elements com l’escriptori, la barra de tasques, el menú d’inici i les finestres de l’explorador de fitxers.
  
* Comentar la millora de fluïdesa en màquines virtuals en alliberar memòria RAM.

 > *Pel que fa a les màquines virtuals, alliberar memòria RAM millora la fluïdesa general perquè el sistema disposa de més recursos disponibles per executar processos.*

## 🔐 Fase 6 – Gestió de permisos (ACLs)

### Què són les ACLs?

A Windows, cada recurs té una **ACL (Access Control List)** que defineix els permisos detallats per a cada identitat (**ACE - Access Control Entry**).

> *Els permisos ACL permeten un control molt més granular que els permisos de xarxa, permetent herències i excepcions per usuari específic.*

### Configuració Pràctica

* **Objectiu:** El grup `Limitats` té accés total a `D:\Projectes`, però l'`alumne2` només pot llegir.
<img width="225" height="33" alt="image" src="https://github.com/user-attachments/assets/71076dd1-e30f-4c0b-b226-3dc4a29f7e35" />

* [ ] **Pas 24.** Crear la carpeta `D:\Projectes` com a administrador.
<img width="319" height="103" alt="image" src="https://github.com/user-attachments/assets/a30aa0c4-7f25-4b3c-9d59-10278fdeee0b" />

* [ ] **Pas 25.** **Assignar permisos al grup:**
1. Propietats → Seguretat → Avançat.
2. Desactivar herència (conservant permisos).
3. Eliminar `Users`/`Everyone`.
4. Afegir grup `Limitats` amb **Control Total**.
<img width="319" height="103" alt="image" src="https://github.com/user-attachments/assets/c16ce7d7-c862-4f47-b508-91e7e1ccc5d3" />



* [ ] **Pas 26.** Verificar amb `alumne1` (ha de poder crear i esborrar).
  <img width="606" height="46" alt="image" src="https://github.com/user-attachments/assets/c5960454-0112-4baf-9703-f284821b6616" />

* [ ] **Pas 27.** **Aplicar excepció per alumne2:**
Executar com administrador:
<img width="555" height="65" alt="image" src="https://github.com/user-attachments/assets/a06d7854-9397-49ed-9ae0-9bb141a7c0e3" />

* [ ] **Pas 28.** Verificar amb `alumne2` (només lectura, denegació en intentar crear fitxers).
<img width="424" height="297" alt="image" src="https://github.com/user-attachments/assets/0a524ba7-6a18-47cd-9986-51fe80417999" />

* [ ] **Pas 29.** Consultar permisos finals:
<img width="597" height="152" alt="image" src="https://github.com/user-attachments/assets/c19e3f4a-1f11-4b8d-8d11-50e12781328f" />

