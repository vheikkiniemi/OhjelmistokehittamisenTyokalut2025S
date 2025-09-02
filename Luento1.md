
> [!NOTE]
> Materiaali luotiin ChatGPT:n ja Copilotin avulla.


---

# 📜 Ohjelmistokehityksen historiaa

1. **Perinteinen vesiputousmalli (1970–1990-luku)**

   * Ohjelmistokehityksessä oli **pitkiä kehitys- ja julkaisu­sarjoja**.
   * Koodi integroitiin harvoin – usein vasta kuukausien kehityksen jälkeen.
   * Tämä johti isoihin “integraatiohelvetteihin”, kun valtava määrä koodia yritettiin yhdistää kerralla.
   * Testaus tapahtui myöhään, jolloin virheet olivat kalliita korjata.

2. **V-malli (1980–2000-luku)**

   * V-malli on **vesiputousmallin laajennus**, jossa testausvaiheet kuvataan rinnakkaisina kehitysvaiheille.
   * Vasemmalla puolella on kehitysvaiheita (määrittely, suunnittelu, toteutus), oikealla vastaavat testausvaiheet (yksikkötestaus, integraatiotestaus, hyväksymistestaus).
   * Ajatus oli tuoda testaus mukaan jo aikaisemmassa vaiheessa, mutta käytännössä se oli silti hyvin jähmeä ja lineaarinen.
   * Toimi paremmin suurissa, turvallisuuskriittisissä järjestelmissä (esim. ilmailu, puolustus, terveydenhuolto).

3. **Iteratiivinen ja ketterä kehitys (1990–2000-luku)**

   * Agile Manifesto (2001) toi idean pienemmistä, nopeammista julkaisuista.
   * Sprintit, jatkuva palaute ja asiakaslähtöisyys ohjasivat kohti automaation tarvetta.
   * Integrointi alkoi tapahtua useammin, mutta silti usein käsin.

4. **Continuous Integration (2000-luvun alku)**

   * Termiä popularisoi Martin Fowler ja ThoughtWorks.
   * Ajatus: kehittäjät yhdistävät koodinsa **päivittäin tai useita kertoja päivässä**.
   * Jenkins (2004, alun perin Hudson) oli keskeinen työkalu CI\:n leviämisessä.
   * Tavoite: “Riko koodisi aikaisin, korjaa se nopeasti.”

5. **Continuous Delivery (2000-luvun loppu)**

   * Jez Humble ja David Farley julkaisivat kirjan *Continuous Delivery* (2010).
   * Korosti, että julkaisemisen tulisi olla toistettavaa, automatisoitua ja riskitöntä.
   * Infrastruktuurin virtualisointi ja pilvipalvelut mahdollistivat nopean ympäristöjen pystyttämisen.

6. **Continuous Deployment (2010-luku →)**

   * Netflix, Amazon ja Facebook ottivat käyttöön mallin, jossa muutokset siirtyvät suoraan tuotantoon automaattisesti.
   * Tämä toi DevOps-kulttuurin: kehitys ja ylläpito sulautuivat yhteen.
   * Konttiteknologiat (Docker 2013, Kubernetes 2014) ja pilviarkkitehtuurit tukivat nopeaa ja skaalautuvaa toimitusta.

---

## 🧩 Kehityspolku mallista toiseen

* **Vesiputous → V-malli:** testaus tuotiin näkyväksi, mutta malli pysyi raskaan lineaarisena.
* **V-malli → Agile:** tarve joustavuuteen ja nopeampaan palautteeseen.
* **Agile → CI:** kehittäjien työ helpottui, kun virheet huomattiin heti.
* **CI → CD (Delivery):** julkaisemisesta tehtiin hallittu ja automatisoitu prosessi.
* **CD (Delivery) → CD (Deployment):** poistettiin viimeinen manuaalinen vaihe → täysin automaattinen tuotantoon vienti.


---

# 🔧 DevOps lyhyesti

**DevOps** on ajattelutapa, kulttuuri ja kokoelma käytäntöjä, jotka yhdistävät **kehityksen (Development)** ja **ylläpidon/toiminnan (Operations)**.

**Tavoite on:**

* lyhentää ohjelmiston toimitusaikoja
* parantaa laatua ja luotettavuutta
* murtaa siilot kehittäjien ja ylläpitäjien välillä

---

## 🎯 DevOpsin perusperiaatteet

1. **Kulttuuri ja yhteistyö**

   * Ei enää “heitä koodi yli aidan ylläpidolle” -ajattelua.
   * Yhteiset tavoitteet: kaikki vastaavat ohjelmiston toimivuudesta.

2. **Automaatio**

   * CI/CD on DevOpsin ytimessä.
   * Testaus, julkaisu, infrastruktuurin hallinta (Infrastructure as Code, IaC) automatisoidaan.

3. **Jatkuva mittaaminen ja palaute**

   * Sovellusten suorituskykyä, virheitä ja käyttäjäkokemusta mitataan reaaliaikaisesti.
   * Palautetta käytetään kehityksen suunnan ohjaamiseen.

4. **Jatkuva oppiminen ja parantaminen**

   * Post-mortem-analyysit virheistä ilman syyllisten etsintää.
   * Iteratiivinen kehitys ja kokeilut.

---

## 🛠️ DevOpsin mahdollistajat

* **Versiohallinta** (GitHub, GitLab)
* **CI/CD-työkalut** (GitHub Actions, Jenkins, Azure DevOps, GitLab CI)
* **Kontit ja orkestrointi** (Docker, Kubernetes)
* **Pilvipalvelut** (AWS, Azure, GCP)
* **Konfiguraation hallinta** (Ansible, Terraform, Puppet, Chef)
* **Monitorointi ja lokitus** (Prometheus, Grafana, ELK, Splunk)

---

## 🌍 Miksi DevOps?

* Nopeammat julkaisut → kilpailuetu
* Parempi skaalautuvuus ja kustannustehokkuus
* Vähemmän virheitä tuotannossa
* Ylläpito ja kehitys samassa rytmissä → jatkuva arvon tuottaminen asiakkaille

---

## 📌 Yhteys CI/CD\:hen

* **CI/CD on DevOpsin konkreettinen käytäntö.**
* DevOps = kulttuuri ja filosofia
* CI/CD = tekninen toteutus, joka tekee DevOpsista käytännössä mahdollisen

---

# 🔐 DevSecOps

**DevSecOps (Development, Security, Operations)** tarkoittaa sitä, että tietoturva ei ole erillinen vaihe kehityksen lopussa, vaan **sisäänrakennettu osa koko ohjelmiston elinkaarta**.

**Perusidea:**

* DevOps + Security = DevSecOps
* “Security as Code” → tietoturva automatisoidaan ja integroidaan samaan pipelineen kuin koodi ja julkaisut


## 🎯 DevSecOpsin periaatteet

1. **Shift Left -ajattelu**

   * Turvallisuus tuodaan jo kehityksen alkuvaiheisiin.
   * Virheet ja haavoittuvuudet pyritään havaitsemaan mahdollisimman aikaisin (halvempaa korjata).

2. **Automaattinen tietoturvatestaus**

   * Staattinen koodianalyysi (SAST)
   * Dynaaminen sovellustestaus (DAST)
   * Haavoittuvuusskannaus (esim. OWASP ZAP, Trivy, Snyk)

3. **Continuous Security**

   * Jokainen commit ja build tarkistetaan automaattisesti.
   * Julkaisut ja ympäristöt valvotaan reaaliajassa.

4. **Yhteinen vastuu**

   * Ei “security team fixaa myöhemmin” -mallia.
   * Kehittäjät, DevOps-tiimit ja tietoturva-asiantuntijat toimivat yhdessä.

---

## 🛠️ Tyypillisiä DevSecOps-työkaluja

* **Koodin tarkistus:** SonarQube, ESLint, Bandit
* **Haavoittuvuusskannerit:** Snyk, OWASP Dependency-Check, Trivy
* **Konttien ja infrastruktuurin tarkistus:** Aqua Security, Anchore, HashiCorp Vault
* **CI/CD-integraatio:** GitHub Actions, GitLab CI, Jenkins + security plugin

---

## 🌍 Miksi DevSecOps?

* Turvallisuus ei ole pullonkaula → julkaisut pysyvät nopeina, mutta turvallisina
* Haavoittuvuudet havaitaan varhaisessa vaiheessa → säästää aikaa ja rahaa
* Asiakasluottamus ja sääntely (GDPR, ISO 27001, NIST) edellyttävät tietoturvaa koko elinkaaren ajan

---

👉 Käytännössä **DevOps → DevSecOps** on siirtymä:

* **DevOps:** Nopeus ja laatu
* **DevSecOps:** Nopeus, laatu ja turvallisuus


Hyvä idea 👌 Tässä on **DevOpsin ja DevSecOpsin keskeinen sanasto** selityksineen. Tämä sopii hyvin esimerkiksi opetukseen tai pikaoppaaksi:

---

# 🔧 DevOps & DevSecOps – keskeinen sanasto

## Peruskäsitteet

* **DevOps**
  Kulttuuri ja käytäntö, jossa **kehitys (Development)** ja **ylläpito (Operations)** yhdistetään. Tavoitteena on nopeampi ja luotettavampi ohjelmiston toimitus.

* **DevSecOps**
  DevOps + **Security**. Tietoturva tuodaan mukaan koko ohjelmiston elinkaareen alusta asti (“shift left”). Turvallisuus on kaikkien vastuulla.

* **CI/CD (Continuous Integration / Continuous Delivery / Deployment)**
  Käytännöt ja työkalut, joilla koodi integroidaan usein ja julkaisut automatisoidaan. Ydinosa DevOpsia.

* **Pipeline**
  Automaattinen prosessiketju, jossa koodi siirtyy vaiheittain (build → test → release → deploy).

---

## DevOps-käytännöt

* **Continuous Integration (CI)**
  Kehittäjät yhdistävät koodinsa usein (päivittäin). Automaattiset testit varmistavat, ettei uusi koodi riko olemassa olevaa.

* **Continuous Delivery (CD)**
  Hyväksytyt muutokset voidaan automaattisesti julkaista testi- tai esituotantoympäristöön.

* **Continuous Deployment (CD)**
  Jokainen hyväksytty muutos etenee automaattisesti tuotantoon ilman manuaalisia vaiheita.

* **Infrastructure as Code (IaC)**
  Infrastruktuuri (palvelimet, verkot, kontit) määritellään koodina (esim. Terraform, Ansible).

* **Monitoring & Logging**
  Sovellusten ja järjestelmien jatkuva seuranta ja lokitietojen analyysi ongelmien havaitsemiseksi.

---

## DevSecOps-käytännöt

* **Shift Left**
  Tietoturva tuodaan kehityksen alkuvaiheisiin, ei jätetä pelkästään testaus- tai tuotantovaiheeseen.

* **SAST (Static Application Security Testing)**
  Staattinen koodin analyysi: etsitään haavoittuvuuksia lähdekoodista ennen ajoa.

* **DAST (Dynamic Application Security Testing)**
  Dynaaminen testaus: sovellusta ajetaan ja testataan ulkopuolelta (esim. OWASP ZAP).

* **Dependency Scanning**
  Tarkistetaan ulkoiset kirjastot ja paketit tunnettuja haavoittuvuuksia vastaan (esim. Snyk, OWASP Dependency-Check).

* **Secrets Management**
  Tunnukset, API-avaimet ja salaisuudet hallitaan turvallisesti (esim. HashiCorp Vault, AWS Secrets Manager).

* **Compliance-as-Code**
  Säännösten ja standardien (esim. GDPR, ISO 27001, NIST) noudattaminen automatisoidusti osana pipelinea.

---

## Työkalut (esimerkit)

* **CI/CD:** Jenkins, GitHub Actions, GitLab CI, Azure DevOps
* **Kontit & orkestrointi:** Docker, Kubernetes, OpenShift
* **Tietoturvatestaus:** OWASP ZAP, SonarQube, Snyk, Trivy
* **Infrastruktuuri:** Terraform, Ansible, Puppet, Chef
* **Monitorointi:** Prometheus, Grafana, ELK-stack

---
