> [!NOTE]
> Materiaali on luotu ChatGPT:n ja Copilotin avulla.

# **🖥️ Johdatus komentoriviin**

## **1. Komentorivi yleisesti**

### **🔹 Historia**

* **1960–1970-luku:** Tietokoneiden käyttö perustui tekstipohjaisiin komentoihin terminaaleissa (esim. UNIX, MS-DOS).
* **1980-luku:** Graafiset käyttöliittymät (GUI) yleistyivät, mutta komentorivit säilyivät tehokäyttäjien työkaluina.
* **Nykyään:** Komentorivi on edelleen keskeinen työkalu ohjelmistokehityksessä, järjestelmänhallinnassa, DevOpsissa ja tietoturvassa.

### **🔹 Mikä juttu?**

* Antaa käyttäjälle tarvittaessa suoran pääsyn käyttöjärjestelmään ja ohjelmiin.
* Mahdollistaa **automaation** ja toistettavat prosessit komento- ja skriptipohjaisesti.

### **🔹 Miksi?**

* **Tehokkuus:** Usein nopeampaa kuin graafisen käyttöliittymän kautta.
* **Automaation mahdollisuus:** Monimutkaisia prosesseja voi ajaa yhdellä skriptillä.
* **Etähallinta:** Palvelimia voidaan hallita verkon yli (esim. SSH).
* **Kattavuus:** Monet järjestelmän toiminnot löytyvät vain komentorivin kautta.
* **Ajattomuus:** Samat komennot voivat toimia vuodesta ja vuosikymmenestä toiseen.

### **🔹 Haasteet**

* **Oppimiskynnys:** Ei yhtä intuitiivinen kuin kuvakkeet ja valikot.
* **Muistettavat komennot:** Paljon eri komentoja ja parametreja.
* **Virhealttius:** Väärä komento voi johtaa suuriin ongelmiin (esim. `rm -rf /`).

> [!TIP]  
> Komentorivin tunteminen on **must**-juttu IT-alalla toimivalle

---

## **2. PowerShell**

### **🔹 Historia**

* Julkaistiin **2006** Microsoftin toimesta.
* Kehitettiin korvaamaan MS-DOS ja vanha Command Prompt (cmd.exe).
* Huhut kertoo, että haluttiin tuoda Linuxista tuttu lähestyminen Windows-ympäristöön.
* Rakennettu **.NET Frameworkin** ja myöhemmin .NET Coren päälle → toimii nykyään myös Linuxissa ja macOS\:ssä.

### **🔹 Mikä juttu?**

* Tehokas työkalu erityisesti **Windows-järjestelmien hallintaan**.
* Käytössä järjestelmänvalvojilla, DevOps-asiantuntijoilla ja pilvipalveluiden hallinnassa.

### **🔹 Yleistä**

* Komennot ovat **objekti-pohjaisia cmdletejä**, esim. `Get-Process`, `Set-Item`.
* Tukee skriptausta (`.ps1`-tiedostot).
* Syvä integraatio Microsoftin ympäristöihin (Active Directory, Azure).

👉 **Esimerkki:**

```powershell
# Näytä käynnissä olevat prosessit
Get-Process

# Luo uusi kansio
New-Item -ItemType Directory -Path "C:\Testi"
```

---

## **3. Bash (Bourne Again SHell)**

### **🔹 Historia**

* Kehitetty **1989** osana GNU-projektia (Brian Fox).
* Korvasi alkuperäisen UNIX Bourne Shellin (sh).
* Nykyään yleisin komentotulkki Linuxissa, käytössä myös macOS\:ssä.

### **🔹 Mikä juttu?**

* Pääsy käyttöjärjestelmän ytimeen ja ohjelmiin tekstipohjaisesti.
* Erittäin tärkeä **Linux-järjestelmänhallinnassa, palvelinten ylläpidossa ja ohjelmistokehityksessä**.

### **🔹 Yleistä**

* Komennot ovat yhdisteltävissä (pipe `|`, uudelleenohjaukset).
* Tukee skriptausta (`.sh`-tiedostot).
* Käytössä laajasti DevOpsissa (Docker, Kubernetes, CI/CD).

👉 **Esimerkki:**

```bash
# Näytä nykyinen kansio
pwd

# Listaa tiedostot koon mukaan
ls -lhS

# Etsi sana "error" tiedostosta
grep "error" loki.txt
```

---

## **4. Python komentorivin työkaluna**

### **🔹 Historia**

* Kehittäjä: **Guido van Rossum**, julkaistu 1991.
* Ei alun perin komentotulkki, mutta nykyään yksi maailman suosituimmista skriptikielistä.
* Pythonia käytetään komentorivin kautta interpreterillä (`python` tai `python3`).

### **🔹 Mikä juttu?**

* Soveltuu komentoriviltä ajettavien skriptien kirjoittamiseen.
* Käytetään paljon **automaation, datankäsittelyn ja web-palveluiden hallintaan**.
* Yhdistää ohjelmoinnin ja komentorivin vahvuudet.

### **🔹 Yleistä**

* Selkeä syntaksi → helppo oppia ja ihastua.
* Laaja kirjastoekosysteemi.
* Toimii sekä pienissä skripteissä että isoissa projekteissa.

👉 **Esimerkki:**

```python
# hello.py
import os

print("Nykyinen kansio:", os.getcwd())

for f in os.listdir("."):
    print(f)
```

```bash
# Aja skripti komentoriviltä
python hello.py
```

---

## **5. Miksi IT-alan opiskelijan tulee osata komentorivi?**

1. **Yleispätevyys:** Bash (Linux), PowerShell (Windows), Python (monialustainen). Kaikissa ympäristöissä komentorivi on keskeinen.
2. **Työelämärelevanssi:** Järjestelmänhallinta, ohjelmistokehitys, tietoturva ja DevOps nojaavat komentorivin käyttöön.
3. **Automaatio:** Toistuvat tehtävät voidaan skriptata → säästää aikaa ja vähentää virheitä.
4. **Ongelmanratkaisu:** Syventää ymmärrystä käyttöjärjestelmästä, verkoista ja prosesseista.
5. **Työmarkkinataidot:** Työnantajat odottavat, että IT-ammattilaiset osaavat käyttää komentoriviä tehokkaasti.

---

## **🔄 PowerShell vs. Bash vs. Python – Yhteenvetotaulukko**

| Ominaisuus / Työkalu | **PowerShell**                                    | **Bash**                                                                             | **Python**                                                                                               |
| -------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| **Historia**         | 2006, Microsoft, korvasi MS-DOS/Command Promptin  | 1989, GNU-projekti, jatkokehitys UNIX-sh\:sta                                        | 1991, Guido van Rossum, yleiskäyttöinen ohjelmointikieli                                                 |
| **Alustat**          | Windows (myös Linux ja macOS nykyään)             | Linux, macOS, myös Windows (WSL/Git Bash)                                            | Monialustainen: Windows, Linux, macOS                                                                    |
| **Päätarkoitus**     | Windowsin hallinta, DevOps, skriptiautomaatio     | Linux/UNIX-järjestelmien hallinta, palvelinten ylläpito                              | Ohjelmointi, automaatio, datankäsittely, skriptit                                                        |
| **Käyttötapa**       | Cmdletit ja objektit (esim. `Get-Process`)        | Tekstipohjaiset komennot ja yhdisteltävyys (esim. `ls -lh`, `grep "error" file.txt`) | Ajetaan Python-tulkin kautta (`python script.py`) tai interaktiivisesti REPL\:ssä (`>>> print("Hello")`) |
| **Skriptaus**        | `.ps1` tiedostot                                  | `.sh` tiedostot                                                                      | `.py` tiedostot                                                                                          |
| **Vahvuudet**        | Syvä integraatio Windowsiin ja Azureen            | Yleisin Linuxissa, tehokkaat yhdistelmät (grep, awk, sed, putket)                    | Selkeä syntaksi, laajat kirjastot, soveltuu kaikkeen pienistä skripteistä isoihin projekteihin           |
| **Esimerkkikomento** | `Get-Process` → listaa prosessit                  | `ls -lhS` → listaa tiedostot koon mukaan                                             | `print("Hello World")`                                                                                   |
| **Kenelle tärkein?** | Järjestelmänvalvojat, Windows- ja pilviympäristöt | Linux-järjestelmän käyttäjät, DevOps                                                 | Kehittäjät, data-analyytikot, automaation rakentajat                                                     |

---


> [!TIP]  
> **PowerShell:** välttämätön, jos työskentelee Microsoftin ympäristöissä (Windows Server, Active Directory, Azure).  
> **Bash:** perusosaaminen vaaditaan kaikilta, jotka käyttävät Linuxia (palvelimet, verkot, tietoturva, DevOps).  
> **Python:** antaa koodaus- ja automaatiotaidot, jotka täydentävät PowerShelliä ja Bashia.  

---

# **🖥️ Komentotulkkien ja komentojen terminologia**

## **1. Komentotulkki (Command-line interpreter, Shell)**

* **Määritelmä:** Ohjelma, joka lukee käyttäjän kirjoittamia komentoja ja välittää ne käyttöjärjestelmälle tai suorittaa ne itse.
* **Esimerkkejä:**

  * **Bash:** Linuxin yleisin komentotulkki.
  * **PowerShell:** Windowsin kehittynyt komentotulkki.
  * **Python-interpreter:** Ohjelmointikielen tulkki, jota voidaan käyttää komentoriviltä.

👉 **Esimerkki (Bash):**

```bash
echo "Hei maailma"
```

Tässä `echo` on komento, jonka komentotulkki suorittaa, ja tulostaa tekstin näytölle.

---

## **2. Komento (Command)**

* **Määritelmä:** Yksittäinen käsky, jonka komentotulkki tunnistaa ja suorittaa.
* **Tyyppejä:**

  * **Sisäiset komennot:** kuuluvat itse komentotulkkiin (esim. `cd` Bashissa tai `Set-Location` PowerShellissä).
  * **Ulkopuoliset komennot:** erillisiä ohjelmia (esim. `python`, `git`, `ping`).

👉 **Esimerkki (PowerShell):**

```powershell
Get-Date
```

Tässä `Get-Date` on **cmdlet**, joka palauttaa järjestelmän nykyisen päivämäärän ja kellonajan.

---

## **3. Komentorivi (Command line)**

* **Määritelmä:** Tekstirivi, johon käyttäjä kirjoittaa komennon.
* **Käytännössä:** Jokainen rivi = yksi käsky. Monimutkaisempia voidaan yhdistellä pipeilla (`|`) tai skripteihin.

👉 **Esimerkki (Bash):**

```bash
ls -lh | grep ".txt"
```

* `ls -lh` listaa tiedostot.
* `|` (pipe) ohjaa tulosteen seuraavalle komennolle.
* `grep ".txt"` suodattaa vain tekstitiedostot.

---

## **4. Parametri / Argumentti (Parameter / Argument)**

* **Määritelmä:** Lisätieto, jota annetaan komennolle sen toiminnan muuttamiseksi.
* **Ero:**

  * Argumentti → usein yleinen lisäarvo (esim. tiedoston nimi).
  * Parametri → voi sisältää lipun (`-l`, `--help`) tai avainsanan.

👉 **Esimerkki (Bash):**

```bash
ls -l /home/user
```

* Komento: `ls`
* Parametri: `-l` (näytä tiedot listamuodossa)
* Argumentti: `/home/user` (kohdekansio)

👉 **Esimerkki (PowerShell):**

```powershell
Get-ChildItem -Path C:\Users -Recurse
```

* Komento: `Get-ChildItem`
* Parametri: `-Path` (määrää polun)
* Argumentti: `C:\Users`

---

## **5. Putki (Pipe `|`)**

* **Määritelmä:** Ohjaa yhden komennon tulosteen seuraavan komennon syötteeksi.
* **Hyöty:** Mahdollistaa komentojen ketjuttamisen tehokkaasti.

👉 **Esimerkki (Bash):**

```bash
ps aux | grep python
```

* `ps aux` listaa prosessit.
* `grep python` etsii niistä Python-prosessit.

👉 **Esimerkki (PowerShell):**

```powershell
Get-Process | Where-Object { $_.CPU -gt 100 }
```

Näyttää vain prosessit, jotka käyttävät yli 100 CPU-yksikköä.

---

## **6. Skripti**

* **Määritelmä:** Tiedosto, joka sisältää sarjan komentoja, suoritettavaksi yhdellä kertaa.
* **Hyöty:** Automatisoi toistuvat tehtävät.

👉 **Esimerkki (Bash-skripti):**

```bash
#!/bin/bash
echo "Aloitetaan varmuuskopiointi..."
tar -czf backup.tar.gz /home/user
echo "Valmis!"
```

👉 **Esimerkki (Python-skripti):**

```python
# backup.py
import shutil

shutil.make_archive("backup", "zip", "/home/user")
print("Varmuuskopio valmis!")
```

---

## **7. Prompt (Komentokehotin)**

* **Määritelmä:** Merkki tai tekstijono, joka kertoo komentotulkin olevan valmis vastaanottamaan komentoja.
* **Esimerkkejä:**

  * Bash: `$` tai `user@host:~$`
  * PowerShell: `PS C:\Users\Ville>`
  * Python REPL: `>>>`

---

# **🎯 Miksi terminologia on tärkeä?**

Kun ymmärrät sanat kuten **komento, argumentti, parametri, pipe ja skripti**, pystyt:

* lukemaan ohjeita ja dokumentaatiota helpommin
* ymmärtämään eri komentotulkkien yhtäläisyyksiä ja eroja
* rakentamaan omia automaatioita selkeästi

---

# 🖥️ Käyttöjärjestelmät ja komentorivit

| Käyttöjärjestelmä                                      | Oletuskomentotulkki                      | Vaihtoehdot / saatavilla olevat komentotulkit                                        | Huomioita                                                                                                                |
| ------------------------------------------------------ | ---------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| **Windows (XP → 10/11)**                               | **Command Prompt (cmd.exe)**             | PowerShell, Git Bash, Bash (WSL), Python REPL                                        | Cmd.exe on vanhin, mutta PowerShell on nykyaikainen ja suositeltu. WSL mahdollistaa aidon Linux Bashin ajon Windowsissa. |
| **Windows Server**                                     | PowerShell                               | Cmd.exe, Bash (WSL), Python                                                          | Ylläpitäjien ensisijainen työkalu on PowerShell.                                                                         |
| **Linux (Ubuntu, Debian, Fedora, CentOS, Arch, jne.)** | **Bash** (tai Dash tietyissä jakeluissa) | Zsh, Fish, Ksh, Tcsh, Python REPL, PowerShell (asennettavissa)                       | Bash on de facto -standardi Linuxissa, mutta monet asentavat Zsh\:n (esim. Oh My Zsh).                                   |
| **macOS (Catalina asti)**                              | **Bash**                                 | Zsh (nykyinen oletus macOS Catalinasta eteenpäin), Fish, Python, PowerShell          | Apple vaihtoi oletus-Bashista Zsh\:iin lisenssisyistä (Catalina 2019).                                                   |
| **FreeBSD / OpenBSD / NetBSD**                         | **sh** tai **tcsh** (riippuu versiosta)  | Bash, Zsh, Ksh, Python, PowerShell (nykyään saatavilla)                              | BSD-maailmassa useampi shell-vaihtoehto, mutta Bash yleensä asennetaan.                                                  |
| **Solaris (Oracle Solaris)**                           | **sh** (Bourne Shell)                    | Bash, Ksh, Python                                                                    | Solaris-järjestelmissä paljon perintöä UNIX-ajalta.                                                                      |
| **AIX (IBM)**                                          | **ksh** (KornShell)                      | Bash, sh, Python                                                                     | KornShell on IBM\:n Unix-järjestelmissä oletus.                                                                          |
| **Android (Linux-pohjainen)**                          | **sh** (Toybox/BusyBox shell)            | Termux (Bash, Zsh, Python), ADB shell                                                | Kehittäjät käyttävät usein Termuxia saadakseen Bashin ja Pythonin.                                                       |
| **iOS / iPadOS**                                       | Ei varsinaista komentoriviä käyttäjälle  | Jailbreakin kautta: Bash, Zsh, Python                                                | Normaalikäytössä ei avoinna komentoriviä.                                                                                |
| **ChromeOS**                                           | Crosh (Chrome Shell)                     | Linux (Crostini) → Bash, Zsh, Python, PowerShell (Linuxin kautta)                    | Crosh on rajoitettu, mutta Linux-tuki avaa laajat komentorivit.                                                          |
| **Haiku OS**                                           | Bash                                     | Zsh, Python                                                                          | Haiku jatkaa BeOSin perintöä, mutta käyttää Bashia.                                                                      |
| **DOS (MS-DOS, FreeDOS)**                              | **COMMAND.COM**                          | Ei oletuksena moderneja, mutta voi asentaa esim. Bash for DOS tai Python DOS-versiot | Historiallisesti DOS toimi komentorivillä.                                                                               |
| **Unix (klassinen)**                                   | sh (Bourne Shell)                        | ksh, csh, tcsh                                                                       | Monet nykyiset shellit pohjautuvat näihin.                                                                               |

---

> [!TIP]  
>  **Windows** → Cmd.exe (vanha) ja PowerShell (nykyinen), sekä mahdollisuus käyttää Bashia (WSL).  
> **Linux & macOS** → Bash ja Zsh hallitsevat, muut vaihtoehtoiset shellit mahdollisia.  
> **Python REPL** on saatavilla **kaikissa ympäristöissä**, joissa Python on asennettu.  
> **Erikoisjärjestelmät (AIX, Solaris, Android)** käyttävät usein perinteisiä shellejä (ksh, sh), mutta vaihtoehdot ovat asennettavissa.  

---

# **🖥️ Visual Studio Code ja komentotulkit**

## **1. PowerShell VS Codessa**

### **Asennus (tarkista ennen asennusta onko jo asennettu)**

**Windows**

1. Asenna **PowerShell 7** (pwsh) → (Microsoft Store tai msi).
2. Avaa VS Code → Extensions (Ctrl+Shift+X) → asenna **“PowerShell” (Microsoft)**.
3. Terminal → **Select Default Profile** → valitse **PowerShell** → **+** avaa uusi terminaali.

**macOS / Linux**

1. Asenna PowerShell 7 paketinhallinnasta (brew/apt/yum/snap).
2. VS Code → Extensions → **PowerShell**.
3. Terminal → Select Default Profile → **pwsh**.

> [!TIP]  
> **Skriptaus ja ajaminen**: `.ps1`-tiedostot, F5/F6, integroidut terminaalit.  
> **Debuggaus**: breakpointit, askellus, **Variables/Call Stack**.  
> **IntelliSense**: cmdletit, parametrit, objektien ominaisuudet.  
> **Linttaus & formatointi**: PSScriptAnalyzer (tulee laajennuksen mukana).  
> **Testaus**: **Pester**-testit integroidulla testinäkymällä.  
> **Automaatio**: **tasks.json** → ajota buildit/deployt PowerShell-skriptein.  

---

## **2. Bash VS Codessa**

### **Asennus (tarkista ennen asennusta onko jo asennettu)**

**Linux/macOS**
– Bash on valmiina. VS Code → Terminal → **Select Default Profile** → **bash**.

**Windows**
Vaihtoehdot:

* **Git Bash**: asenna **Git for Windows**, saat “Git Bash”-profiilin.
* **WSL**: asenna **Windows Subsystem for Linux** (+ distro), VS Code tunnistaa **wsl**-profiilin.
* Terminal → Select Default Profile → valitse **Git Bash** tai **WSL: Ubuntu**.

*(Valinnaiset lisät)*

* **ShellCheck** (linttaus): Extensions → “ShellCheck”.
* **bash-language-server** (automaattinen täydennys): Extensions → “Bash IDE” tms.

> [!TIP]  
> **Komennot & skriptit**: `.sh`-tiedostot, shebang `#!/usr/bin/env bash`, `chmod +x`.  
> **Debuggaus**: “Bash Debug” -laajennus (breakpointit perusskripteille).  
> **Linttaus**: ShellCheck korjaa tyypilliset virheet.  
> **DevOps-työ**: Docker/Kubernetes/Ansible/Make suoraan terminaalissa.  
> **Tasks**: `tasks.json` → määritä build/test/format (esim. `bash scripts/build.sh`).  

---

## **3. Python VS Codessa**

### **Asennus (tarkista ennen asennusta onko jo asennettu)**

1. Asenna **Python 3** (Windows Store / python.org / paketinhallinta).
2. VS Code → Extensions → **“Python” (Microsoft)** ja **“Pylance”**.
3. Valitse tulkki: Command Palette (Ctrl+Shift+P) → **Python: Select Interpreter**.
4. (Suositus) Luo virtuaaliympäristö:

```bash
# Windows (PowerShell)
python -m venv .venv
. .\.venv\Scripts\Activate.ps1

# macOS/Linux
python3 -m venv .venv
source .venv/bin/activate
```

VS Code tunnistaa `.venv` automaattisesti.

*(Valinnaiset lisät)*

* **Jupyter** (notebookit), **Black**/**Ruff** (formatointi/linttaus), **pytest**.

> [!TIP]  
> **Ajo & debug**: F5, launch.json, breakpointit, muuttujien tarkastelu.  
> **IntelliSense** (Pylance): tyypit, docstringit, koodinavigointi.  
> **Testit**: unittest/pytest, Test Explorer.  
> **Notebookit**: `.ipynb` Jupyter-ympäristössä (graafit, data-analytiikka).  
> **Refaktorointi**: rename symbol, extract method, import-autot.  
> **Tyylit**: Black/autopep8, Ruff/Flake8.  

---

## **4. Nopeat tarkistukset (toimiiko?)**

**PowerShell-terminaalissa**

```powershell
$PSVersionTable.PSVersion
Get-ExecutionPolicy
```

**Bash-terminaalissa**

```bash
echo $SHELL
bash --version
```

**Python**

```bash
python --version
python -c "print('OK from VS Code')"
```
---

## **🖱️ Pikanäppäimiä**

* **Ctrl+\`** → avaa integroitu terminaali
* **Ctrl+Shift+P** → Command Palette
* **F5** → aja/debuggaa ohjelma
* **Ctrl+K Ctrl+S** → näppäinkomentojen haku
* **Alt+Shift+F** → koodin automaattinen muotoilu

---

## **Mitä näillä kolmella yhdessä saat VS Codessa?**

* **Monialustainen automaatio**: PowerShell (Windows-hallinta), Bash (Linux/DevOps), Python (liima + logiikka).
* **Täysi kehityskierto**: koodi → linttaus/formatointi → testaus → debug → paketointi → deploy (Tasks/terminals/launch).
* **Opetuksessa**: helppo näyttää samat tehtävät kolmella kielellä/kuorella, vertailla syntaksia ja painottaa oikeaa työkalua oikeaan tarkoitukseen.