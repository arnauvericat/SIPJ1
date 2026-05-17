# Exercici 1. Monitorització bàsica de Windows Server

## Objectiu
Monitoritzar l'estat del servidor utilitzant eines integrades de Windows Server.

## Pas a pas

### 1. Obrir el Monitor de recursos
<img width="781" height="591" alt="image" src="https://github.com/user-attachments/assets/0735209e-1b44-486a-b4df-a832bf04aa1c" />


### 2. Revisar l'ús de CPU
Comprova:
* Processos que consumeixen més CPU
* Percentatge total d'ús
<img width="1898" height="359" alt="image" src="https://github.com/user-attachments/assets/da2a50ad-d801-4ebf-b6e2-1ee30920dd68" />

*Fes una captura.*

### 3. Revisar la memòria RAM
Accedeix a la pestanya "Memòria".
Comprova:
* Memòria utilitzada
* Memòria lliure

<img width="1900" height="449" alt="image" src="https://github.com/user-attachments/assets/74932966-e7b0-4b9e-a52d-567e84b7530c" />


### 4. Revisar el disc
Accedeix a "Disc".
Comprova:
* Processos amb més lectura/escriptura
* Activitat del disc
<img width="1900" height="314" alt="image" src="https://github.com/user-attachments/assets/01936281-d9bf-4ff7-9274-f3cd2292a639" />

### 5. Revisar la xarxa
Accedeix a "Xarxa".
Comprova:
* Programes que utilitzen la xarxa
* Velocitat d'enviament i recepció
<img width="1902" height="589" alt="image" src="https://github.com/user-attachments/assets/a43bf256-94f3-48e7-87c8-ca31a3ca6774" />

### 6. Revisar els esdeveniments del sistema
Obre:
* Administrador del servidor $\rightarrow$ Eines $\rightarrow$ Visor d'esdeveniments

Consulta:
* Errors del sistema
* Advertiments
* Errors d'aplicació
<img width="615" height="82" alt="image" src="https://github.com/user-attachments/assets/7e015d6b-915d-4318-8af7-dfb4f0fad22e" />

# Exercici 2. Connexió remota a Windows Server

## Objectiu
Configurar i utilitzar l'Escriptori remot per connectar-se a un Windows Server des d'un altre equip.

## Part 1. Configuració del servidor

### 1. Obrir la configuració d'Escriptori remot
Al servidor:
* Inici $\rightarrow$ Configuració $\rightarrow$ Sistema $\rightarrow$ Escriptori remot

### 2. Activar l'Escriptori remot
Activa:
* Habilitar Escriptori remot

Prem:
* Confirmar
<img width="615" height="130" alt="image" src="https://github.com/user-attachments/assets/7e0d2a1e-d622-46d4-94bb-83959bfe97aa" />

### 3. Permetre usuaris remots
A la mateixa finestra, prem:
* Selecciona els usuaris que poden accedir remotament

Prem:
* Afegir

Escriu el nom de l'usuari que podrà connectar-se.
Prem:
* Comprova els noms

Si l'usuari existeix correctament, prem:
* Acceptar

### 4. Comprovar el nom del servidor
Obre el símbol del sistema:
<img width="285" height="43" alt="image" src="https://github.com/user-attachments/assets/82ced71f-86e2-4720-adac-bd84c18928db" />

### 5. Comprovar la direcció IP del servidor
Al símbol del sistema executa:


Busca:
* Adreça IPv4

Anota la direcció IP.
<img width="513" height="21" alt="image" src="https://github.com/user-attachments/assets/cdf4885c-aa18-46d3-b692-daa0b5ddfaaa" />

### 6. Comprovar el Firewall
Obre:
* Panell de control $\rightarrow$ Sistema i seguretat $\rightarrow$ Firewall de Windows Defender

Prem:
* Permetre una aplicació o característica a través del Firewall

Comprova que:
* Escriptori remot
està permès.
<img width="534" height="23" alt="image" src="https://github.com/user-attachments/assets/da49fade-be19-4bfb-b9ff-6065b81851e5" />

## Part 2. Connexió des del client

### 7. Obrir Connexió a Escriptori remot
Al client:
* Win + R
* Escriu: `mstsc`
* Prem Enter.

### 8. Escriure el nom o la IP del servidor
Introdueix:
* el nom del servidor
* O
* la direcció IP del servidor

Prem:
* Connecta
  <img width="308" height="51" alt="image" src="https://github.com/user-attachments/assets/f2e38976-e876-4219-973d-6e783b1a91a6" />

### 9. Introduir les credencials
Escriu:
* nom d'usuari
* contrasenya
<img width="454" height="429" alt="image" src="https://github.com/user-attachments/assets/c59278a7-6a40-441c-9402-8c8ce5e773d4" />

Prem:
* Acceptar

### 10. Acceptar l'avís de connexió
Si apareix un avís de seguretat:
* marca l'opció per no tornar a mostrar-lo
* prem "Sí"

### 11. Verificar la connexió
Comprova que:
* apareix l'escriptori del servidor
<img width="1919" height="1027" alt="image" src="https://github.com/user-attachments/assets/609b8267-e967-4a46-b6d6-dd49d419793d" />

* pots obrir carpetes
<img width="949" height="754" alt="image" src="https://github.com/user-attachments/assets/42ac8b4d-9e8b-44e0-98d2-9b0577a0e500" />

* pots obrir l'Administrador del servidor
<img width="946" height="757" alt="image" src="https://github.com/user-attachments/assets/5a80e519-ba5b-4f24-b903-460ef19b78e0" />

## Part 3. Tancar la sessió

### 12. Tancar la connexió remota
Al servidor remot:
* Inici $\rightarrow$ Tanca sessió
<img width="344" height="150" alt="image" src="https://github.com/user-attachments/assets/971d704b-d0a4-4999-a49b-82b46c7c58ff" />

# Exercici 3. Consulta de llicències de Windows Server i equips units al domini

## 1. Preu aproximat de les llicències

| Producte | Preu aproximat |
|---|---|
| Windows Server 2022 Standard | 250 € |
| Windows Server 2022 Datacenter | 300 € |
| User CAL | 35 € |
| Device CAL | 45 € |

> Els preus són aproximats i poden variar segons el tipus de llicència (OEM, Retail, ESD o volum). :contentReference[oaicite:0]{index=0}

---

## 2. Explicació de les CAL

### Què és una CAL?

Una **CAL** (*Client Access License*) és una llicència que permet que un usuari o dispositiu accedeixi als serveis d'un servidor Windows Server.

Sense CAL, els equips o usuaris no poden utilitzar legalment els serveis del domini, carpetes compartides, impressores o altres recursos del servidor.

### Diferència entre User CAL i Device CAL

| Tipus | Descripció |
|---|---|
| User CAL | La llicència està associada a un usuari. L'usuari pot accedir des de diversos dispositius. |
| Device CAL | La llicència està associada a un dispositiu. Diversos usuaris poden utilitzar el mateix equip. |

---

## 3. Càlcul del cost aproximat

### Dades de l'empresa

- 1 servidor Windows Server
- 25 ordinadors
- 10 portàtils
- 32 usuaris
- Tots els equips units al domini

### Total de dispositius

25 + 10 = **35 dispositius**

---

## Opció A: User CAL

### Cost del servidor

- Windows Server Standard = **250 €**

### Cost de les CAL

- 32 usuaris × 35 € = **1.120 €**

### Cost total

| Concepte | Cost |
|---|---|
| Windows Server Standard | 250 € |
| 32 User CAL | 1.120 € |
| **Total** | **1.370 €** |

---

## Opció B: Device CAL

### Cost del servidor

- Windows Server Standard = **250 €**

### Cost de les CAL

- 35 dispositius × 45 € = **1.575 €**

### Cost total

| Concepte | Cost |
|---|---|
| Windows Server Standard | 250 € |
| 35 Device CAL | 1.575 € |
| **Total** | **1.825 €** |

---

## 4. Model més adequat

El model més adequat per a aquesta empresa és **User CAL**.

### Justificació

L'empresa té:
- 32 usuaris
- 35 dispositius

Alguns usuaris poden utilitzar més d'un equip (ordinador i portàtil). Amb **User CAL**, cada usuari pot connectar-se des de qualsevol dispositiu sense necessitat de comprar una llicència per cada equip.

A més:
- és més econòmic
- és més flexible
- facilita la gestió de llicències

Per això, la millor opció és utilitzar **User CAL**.

---

## 5. Mostrar els equips del domini

### Des d'Active Directory

1. Obrir:
   - **Server Manager**
   - **Tools**
   - **Active Directory Users and Computers**

2. Entrar a:
   - **Computers**
  #### Ordinadors
  <img width="428" height="506" alt="image" src="https://github.com/user-attachments/assets/fa3f6c91-2b20-404a-a78c-5babec1ff67e" />

##### Portatils
 <img width="388" height="244" alt="image" src="https://github.com/user-attachments/assets/93f1fb74-1678-4cdf-b198-a0593bd5c5a7" />


3. Es mostraran tots els equips units al domini.
<img width="370" height="619" alt="image" src="https://github.com/user-attachments/assets/3d20667a-7baa-4184-abd5-24a37491926d" />

