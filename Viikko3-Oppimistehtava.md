> [!NOTE]
> Materiaali on luotu ChatGPT:n ja Copilotin avulla.

# Oppimistehtävä: Komentorivi tutuksi

## 🎯 Tavoite
- Ottaa käyttöön kolme eri komentotulkkia Visual Studio Codessa: **PowerShell**, **Git Bash** ja **Python**.
- Harjoitella komentorivin peruskäyttöä esim. Microsoft Learn -ympäristössä.
- Ymmärtää eri komentotulkkien rooli ohjelmistokehittäjän työkalupakissa.

---

## 🧰 1. tehtävä: Komentotulkit Visual Studio Codessa
1. Avaa **Visual Studio Code**.
2. Ota käyttöön seuraavat komentotulkit:
   - **PowerShell**  
   - **Git Bash** (tarvitset Gitin asennettuna: https://git-scm.com/)  
   - **Python** (tarvitset Pythonin asennettuna: https://www.python.org/)  
3. Luo uusi **Terminal**-ikkuna jokaiselle komentotulkille.  
4. Suorita jokaisessa terminaalissa versiotarkistus:

   ### PowerShell
   - Komentoriviltä:
     ```powershell
     $PSVersionTable.PSVersion
     ```
   - (PowerShellissa ei ole erillistä “sisäistä tulkkia”, joten tämä riittää.)

   ### Git Bash
   - Bashin sisältä:
     ```bash
     echo $BASH_VERSION
     ```

   ### Python
   - Pythonin tulkin sisältä (kun näkyy `>>>`):
     ```python
     import platform
     platform.python_version()
     ```
     tai
     ```python
     import sys
     sys.version
     ```

5. Ota **yksi kuvakaappaus**, josta näkyy kaikki kolme komentotulkkia ja niiden versiotiedot.

---

## 📚 2. tehtävä: Komentotulkkien opiskelu
1. Käytä **Microsoft Learn** -ympäristöä ja opiskele aiheeseen liittyvää materiaalia:
   - [PowerShell](https://learn.microsoft.com/en-us/training/paths/powershell/)
   - [Bash](https://learn.microsoft.com/en-us/training/paths/shell/)
   - [Python](https://learn.microsoft.com/en-us/shows/intro-to-python-development/)
2. Voit myös käyttää mitä tahansa ympäristöä, sivustoa tai tapaa.
3. Opiskele aihetta yhteensä noin **4 tunnin ajan** (voit jakaa ajan eri komentotulkkien välillä).
4. Tee muistiinpanoja oppimastasi.
5. Palauta seuraavan mukainen raportti Itslearningiin. 

**Raportti**: Kirjoita **lyhyt raportti 2-3 kappaletta**, jossa kerrot:
- Mitä komentotulkkien käyttöä harjoittelit?
- Mitä eroja ja yhtäläisyyksiä havaitsit komentotulkkien välillä?
- Mitä uutta opit?

---

## 📤 Palautus
Palauta Itslearningiin:
1. Kuvakaappaus, josta näkyy PowerShell, Git Bash ja Python Visual Studio Codessa (versiot tarkistettu).
2. Raportti opiskelusta suoraan "Vastaan tehtävänantoon" ja sieltä "Vastaus" -laatikkoon

---