
> [!NOTE]
> Materiaali on luotu ChatGPT:n ja Copilotin avulla.

# **📜 Git ja CI/CD**

## **1. Ohjelmistokehityksen historiaa**

* **1960–1980-luku:**

  * Ohjelmat olivat usein yhden ihmisen tekemiä, ja ne ajettiin suurilla tietokoneilla (mainframe).
  * Koodi tallennettiin rei’itettyihin kortteihin tai tiedostoihin → versiohallinta ei ollut ongelma, koska tekijöitä oli vähän.

* **1980–1990-luku:**

  * Ohjelmistot kasvoivat ja tiimit kasvoivat → useampi ihminen muokkasi samoja tiedostoja.
  * Käytettiin versiohallintaa, kuten **RCS** ja **CVS**, jotka tallensivat muutoksia keskitetysti.
  * Ongelmana oli, että vain yksi kehittäjä pystyi muokkaamaan tiedostoa kerrallaan → hidasta ja kömpelöä.

* **2000-luku:**

  * Tuli **Subversion (SVN)**: vähän joustavampi, mutta edelleen keskitetty.
  * Jos keskitetty palvelin kaatui → kaikki pysähtyi.

* **2005: Git syntyy**

  * Linus Torvalds kehitti Gitin Linux-käyttöjärjestelmän hallintaan.
  * Git on **hajautettu**: jokaisella kehittäjällä on oma täydellinen kopio koodihistoriasta.
  * Tämä ratkaisi monia ongelmia: voi työskennellä offline, muutokset voi yhdistää joustavasti, ja historia on turvassa useissa koneissa.

---

## **2. Git ohjelmistokehityksessä**

* Ohjelmistot ovat nykyään usein **yhteistyötä** → useita tekijöitä, eri paikoissa, eri aikoina.
* Git mahdollistaa:

  * **Muutosten historian**: kuka muutti, mitä ja miksi.
  * **Palauttamisen**: jos virhe tapahtuu, palataan edelliseen versioon.
  * **Haaroittamisen**: voidaan kokeilla uutta ilman, että rikotaan “pääversio”.

---

### **2.1. Gitin keskeiset tekijät ja toiminnot**

* **Paikallinen Git**

  * `git init`, `git add`, `git commit`
* **Etärepo (GitHub, GitLab, Bitbucket)**

  * `git push`, `git pull`
* **Branchit**

  * mahdollistavat rinnakkaisen kehityksen
* **Yhdistäminen** (`merge` / `pull request`)

  * koodin tuominen takaisin yhteiseen runkoon

---

### **2.2. Esimerkki tiimityön mallista**

**1. Jokainen kehittäjä kloonaa repon**

* **Mitä tapahtuu:**

  * GitHubissa (tai muussa palvelussa) on **etärepo** – keskitetty kopio projektista.
  * Kun kehittäjä tekee `git clone https://github.com/user/repo.git`, Git kopioi koko historian omalle koneelle.
* **Missä tapahtuu:**

  * GitHub säilyttää pääkopion pilvessä.
  * Kehittäjällä on täydellinen paikallinen kopio (kaikki commitit, kaikki branchit).
* **Miksi tärkeää:**

  * Jokainen voi työskennellä itsenäisesti, jopa ilman nettiä.

---

**2. Tehdään omia muutoksia → commit → push**

* **Mitä tapahtuu:**

  1. Kehittäjä muokkaa tiedostoja paikallisesti.
  2. `git add` kertoo Gitille, mitkä tiedostot halutaan seuraavaan snapshotiin (tilannekuvaan).
  3. `git commit` tallentaa muutoksen paikalliseen historiaan – Git kirjaa:

     * muutoksen sisällön
     * tekijän
     * ajan
     * commit-viestin
  4. `git push` lähettää nämä muutokset GitHubiin (etärepoon).
* **Missä tapahtuu:**

  * Commitit tallentuvat ensin **kehittäjän koneelle** (paikallinen repo).
  * Push siirtää ne **GitHubin etärepoon**, jolloin muutkin näkevät muutokset.
* **Miksi tärkeää:**

  * Kaikki commitit tallentavat täsmällisen historian → voidaan jäljittää virheet ja peruuttaa tarvittaessa.

---

**3. Git tallentaa historian, joten virheistä voi palata taaksepäin**

* **Mitä tapahtuu:**

  * Jokaisella commitilla on yksilöllinen tunniste (hash).
  * Git säilyttää koko kehityshistorian, ei vain viimeisintä versiota.
  * Jos tulee virhe, voidaan tehdä `git checkout <commit-id>` tai `git revert` ja palata toimivaan tilaan.
* **Missä tapahtuu:**

  * Historia on tallessa sekä paikallisessa että etärepossa.
* **Miksi tärkeää:**

  * Ei enää “final\_version2\_final\_really.docx” -tyyppistä kaaosta.
  * Kehitystä voi aina seurata ja dokumentoida.

---

**4. Pull Request (PR) mahdollistaa koodin tarkastelun ennen yhdistämistä**

* **Mitä tapahtuu:**

  * Kehittäjä tekee työnsä omassa branchissa (`feature-login`).
  * Kun työ on valmis, hän avaa **Pull Requestin (PR)** GitHubissa.
  * Tiimikaverit voivat:

    * lukea koodin
    * kommentoida
    * pyytää muutoksia
  * Jos kaikki on ok → PR hyväksytään ja yhdistetään `main`-haaraan.
* **Missä tapahtuu:**

  * Tämä tapahtuu **GitHubin verkkokäyttöliittymässä**, ei komentorivillä.
* **Miksi tärkeää:**

  * Mahdollistaa **koodikatselmoinnin**: kukaan ei vie rikkinäistä koodia pääversioon yksinään.
  * Takaa laadun ja yhteistyön.

---

## **3. Kehitysympäristöjen muutos**

**Ennen:**

* Kehittäjät käyttivät **raskaita IDE-ympäristöjä** kuten Visual Studio tai Eclipse.
* Asennus vei aikaa: piti ladata gigatavujen ohjelmisto, lisätä laajennuksia ja asetuksia.

**Nyt:**

  * **Kevyemmät editorit** (Visual Studio Code, Atom, Sublime Text).
  * VS Code julkaistiin 2015, avoimen lähdekoodin projekti Microsoftilta.
  * Suunniteltu moderniksi, laajennettavaksi ja monialustaiseksi (Windows, macOS, Linux).
  * Miksi VS Code menestyi?

    * Helppo käyttää aloittelijoille
    * Tuki kymmenille ohjelmointikielille
    * **Extensions** (esim. Live Server) tekevät siitä joustavan
    * Integroitu Git-tuki → commitit suoraan editorista
    * Ilmainen ja kevyt

---

### **3.1. Visual Studio Code ja Git – miten ne yhdistyvät?**

**Ennen:**
* Versiohallinta (Git, SVN, CVS) oli erillinen työkalu, jota käytettiin komentoriviltä.
* Commitin tekeminen vaati komentorivin käyttöä → aloittelijoille vaikeaa.
* Kehittäjä joutui usein hyppimään eri työkalujen välillä (editori, komentorivi, versionhallintaohjelma).

**Nyt (Visual Studio Code + Git):**
* Git-tuki on sisäänrakennettu: commit, branchit ja push onnistuvat suoraan käyttöliittymästä.
* Source Control -paneeli näyttää selkeästi kaikki muutokset (vihreä = uusi, punainen = poistettu, keltainen = muokattu).
* Aloittelijan ei tarvitse heti opetella kaikkia Git-komentoja → voi tehdä perustoiminnot painikkeilla.
* Lisäominaisuudet (esim. GitLens-laajennus) tuovat näkyviin, kuka muutti mitä ja milloin.
* Lopputulos: **sama ohjelma hoitaa koodauksen + versionhallinnan**, joten aloittaminen on helppoa ja nopeaa.

---

## **4. CI/CD – mistä siinä on kyse?**

**Ennen CI/CD\:tä (1990-luvulle asti):**

  * Ohjelmistoja julkaistiin harvoin (puolen vuoden välein, jopa kerran vuodessa).
  * Kun kaikki koodi yhdistettiin → tuli valtava “integraatiohelvetti”.
  * Testit ajettiin vasta lopussa → virheet löytyivät myöhään ja niiden korjaaminen oli kallista.

**Continuous Integration (CI):**

  * Jokainen muutos testataan heti, kun se pusketaan koodivarastoon.
  * Varmistaa, että ohjelma pysyy toimintakuntoisena.

**Continuous Delivery / Deployment (CD):**

  * Sovellus voidaan julkaista automaattisesti, ilman käsityötä.
  * Muutokset etenevät nopeasti käyttäjille.


**Esimerkkiarkkitehtuuri:**

1. Kehittäjä pushaa koodin GitHubiin
2. CI-prosessi käynnistyy (testit, tarkistukset, build)
3. Jos onnistuu → CD vie muutoksen tuotantoon / julkaisuun

---

## **5. Miksi GitHub Actions?**

* GitHub on jo monille tuttu → Actions on sisäänrakennettu CI/CD-työkalu.
* Voi automatisoida:

  * Koodin testauksen
  * Linttauksen (koodin siisteyden tarkistamisen)
  * Julkaisun (GitHub Pages, Docker, pilvipalvelut)
* Ei tarvitse omaa palvelinta → GitHub hoitaa ajamisen.
* Perusidea: **Workflow** = joukko automatisoituja tehtäviä
* Workflow sijaitsee `.github/workflows/*.yml`
* Käynnistyy esim. `push`-tapahtumasta

---

**Yksinkertainen esimerkki:**

```yaml
name: Demo workflow
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: echo "Hello Actions!"
```
---
**Esimerkki oppimistehtävästä:**

* Teet muutoksen `index.html` → `push` GitHubiin
* GitHub Actions käynnistyy → tarkistaa ja julkaisee automaattisesti
* GitHub Pages näyttää uuden version selaimessa

---

## **6. Yhteenveto**

* Git ratkaisee ongelman: **miten hallita ja yhdistää koodimuutoksia**.
* CI/CD ratkaisee ongelman: **miten varmistaa laatu ja julkaista nopeasti**.
* Visual Studio Code on työkalu, joka yhdistää nämä: **helppo aloittaa, ammattimainen käytössä**.
* GitHub Actions tuo automaation → **ei enää erillisiä manuaalisia vaiheita**