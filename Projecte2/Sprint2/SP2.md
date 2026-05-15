Aquí tens el text estructurat en format **Markdown** professional, ideal per a un fitxer `README.md` o la documentació d'un repositori a GitHub. He utilitzat encapçalaments, llistes de tasques, blocs de codi i cites per fer-lo més llegible.

---

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
<img width="361" height="497" alt="shot_1778843999" src="https://github.com/user-attachments/assets/3d6c13c2-811b-4520-8097-b21310858df0" />
<img width="562" height="46" alt="shot_1778843788" src="https://github.com/user-attachments/assets/0d496bd8-cf85-4c99-b4b0-d34935420526" />

## 👥 Fase 2 – Quotes i usuaris

* [ ] **Pas 5.** Activar les **quotes de disc** a la partició `Dades` (NTFS).
* [ ] **Pas 6.** Establir un límit de **300 MB** per usuari amb notificació d’advertència.
<img width="361" height="497" alt="shot_1778843999" src="https://github.com/user-attachments/assets/f81b85df-ce05-4490-928d-f9ff078a6b84" />

* [ ] **Pas 7.** Crear dos usuaris locals: `alumne1` i `alumne2`.
* [ ] **Pas 8.** Crear un grup anomenat `Limitats` i afegir-hi ambdós usuaris.
* [ ] **Pas 9.** Provar la còpia de fitxers a `Dades` fins a superar el límit per verificar el bloqueig de la quota.

## 📜 Fase 3 – Script de còpia i automatització

* [ ] **Pas 10.** Afegir un tercer disc virtual i formatar-lo en NTFS com a `Backups`.
* [ ] **Pas 11.** Crear la carpeta `CòpiesUsuaris` dins de la unitat de `Backups`.
* [ ] **Pas 12.** Crear un script `.bat` amb el següent contingut:
```batch
@echo off
xcopy "C:\Users\%USERNAME%" "E:\CòpiesUsuaris\%USERNAME%" /E /I /Y

```


* [ ] **Pas 13.** Obrir `gpedit.msc` → *Configuració d’usuari* → *Scripts* → *Inici de sessió*.
* [ ] **Pas 14.** Assignar l’script perquè s’executi automàticament en iniciar la sessió els usuaris.

## 🔍 Fase 4 – Verificació i documentació

* [ ] **Pas 15.** Iniciar sessió amb `alumne1` i realitzar les comprovacions:
* L'script s'ha executat i ha creat la còpia a `Backups`.
* La quota a `Dades` funciona correctament.



## ⚡ Fase 5 – Gestió de processos i serveis

### Pas 19. Llistar processos actius

1. Inicia sessió com `alumne1`.
2. Obre la consola (`cmd`).
3. Executa i exporta el llistat:
```cmd
tasklist > C:\Users\%USERNAME%\processos_inici.txt

```



### Pas 20. Identificar processos prescindibles

| Nom del procés | Memòria usada | Justificació per eliminar-lo |
| --- | --- | --- |
| `OneDrive.exe` | *Variable* | Sincronització de núvol no necessària en entorn local. |
| `Teams.exe` | *Alta* | Consum excessiu de RAM per a tasques d'administració. |
| `SkypeApp.exe` | *Baixa* | Aplicació de comunicació no requerida. |

### Pas 21. Eliminar processos manualment

Executa per tancar processos innecessaris:

```cmd
taskkill /IM OneDrive.exe /F

```

*Nota: Cal fer captura de pantalla del `tasklist` abans i després.*

### Pas 22. Automatització

Modifica l'script d'inici de sessió afegint:

```batch
taskkill /IM OneDrive.exe /F
taskkill /IM Teams.exe /F

```

### Pas 23. Documentació de rendiment

* Explicar l'efecte de matar processos crítics com `explorer.exe` (es perd la interfície gràfica).
* Comentar la millora de fluïdesa en màquines virtuals en alliberar memòria RAM.

## 🔐 Fase 6 – Gestió de permisos (ACLs)

### Què són les ACLs?

A Windows, cada recurs té una **ACL (Access Control List)** que defineix els permisos detallats per a cada identitat (**ACE - Access Control Entry**).

> [!IMPORTANT]
> Els permisos ACL permeten un control molt més granular que els permisos de xarxa, permetent herències i excepcions per usuari específic.

### Configuració Pràctica

* **Objectiu:** El grup `Limitats` té accés total a `D:\Projectes`, però l'`alumne2` només pot llegir.
* [ ] **Pas 24.** Crear la carpeta `D:\Projectes` com a administrador.
* [ ] **Pas 25.** **Assignar permisos al grup:**
1. Propietats → Seguretat → Avançat.
2. Desactivar herència (conservant permisos).
3. Eliminar `Users`/`Everyone`.
4. Afegir grup `Limitats` amb **Control Total**.


* [ ] **Pas 26.** Verificar amb `alumne1` (ha de poder crear i esborrar).
* [ ] **Pas 27.** **Aplicar excepció per alumne2:**
Executar com administrador:
```cmd
icacls "D:\Projectes" /grant:r alumne2:(R)

```


* [ ] **Pas 28.** Verificar amb `alumne2` (només lectura, denegació en intentar crear fitxers).
* [ ] **Pas 29.** Consultar permisos finals:
```cmd
icacls "D:\Projectes"

```



---

*Documentació generada per a pràctiques d'Administració de Sistemes Operatius.*
