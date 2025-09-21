> [!NOTE]
> Materiaali on luotu ChatGPT:n ja Copilotin avulla.

# **🛡️ Kehitysympäristön eristäminen**

## **1. Mitä on sandboxing?**

**Sandboxing** tarkoittaa eristämistä: ohjelmaa, prosessia tai sovellusta ajetaan hallitussa, rajatussa ympäristössä, jossa se ei voi vahingoittaa muuta järjestelmää.

### **Historia ja tausta**

* **1960–1970-luku:** Ensimmäiset moniajo- ja monikäyttäjäjärjestelmät (esim. UNIX) loivat tarpeen eristää käyttäjien prosessit toisistaan.
* **1990-luku:** Internetin kasvu toi uuden riskin – haitallinen koodi saattoi tulla selaimen kautta. Ensimmäiset "sandbox-selainratkaisut" (esim. Java Applet sandbox).
* **2000–2010-luku:** Turvallisuusuhkien kasvu ja virtualisointiteknologioiden kehitys johtivat kehittyneisiin sandbox-ratkaisuihin (esim. Google Chrome käytti jokaiselle välilehdelle omaa sandboxia).
* **Nykyään:** Sandboxing on olennainen osa sovellusturvaa, haittaohjelmien analyysiä ja pilvipohjaista infrastruktuuria.

### **Miksi sandboxingia käytetään?**

* Suojaa järjestelmää haitalliselta koodilta.
* Mahdollistaa epäluotettavan ohjelman turvallisen testauksen.
* Mahdollistaa kehittäjille ohjelmien ajon hallitussa ympäristössä.

---

## **2. Virtualisointi ja sen muodot sandboxingin yhteydessä**

Sandboxing liittyy tiiviisti virtualisointiin, sillä molemmat perustuvat eristämiseen. Virtualisointi voidaan toteuttaa eri tasoilla:

### **Koneella tehtävä virtualisointi**

Koko käyttöjärjestelmä tai sen osa eristetään ajamaan virtuaalisesti.

* **Tekniikka:** Hypervisorit (esim. Type 1 = suoraan rautaan, Type 2 = käyttöjärjestelmän päällä).
* **Esimerkki tuotenimi:**

  * **VirtualBox** (Type 2 hypervisor): Mahdollistaa useiden käyttöjärjestelmien ajamisen yhdellä koneella.

### **Konttipohjainen virtualisointi**

Kevyempi eristystekniikka, jossa sovellukset ja niiden riippuvuudet pakataan konttiin. Kontit jakavat käyttöjärjestelmän ytimen, mutta pysyvät erillään toisistaan.

* **Tekniikka:** Namespacet ja cgroups (Linux).
* **Esimerkki tuotenimi:**

  * **Docker**: Suosituin konttialusta, mahdollistaa sovellusten siirrettävyyden ja skaalautuvuuden.

### **Pilvipalveluissa tapahtuva virtualisointi**

Pilvipalveluntarjoajat hyödyntävät virtualisointia ja konttiteknologioita skaalautuvien palveluiden tarjoamiseen.

* **Esimerkki tuotenimiä (Azure):**

  * **Azure Virtual Machines (VMs):** Tarjoaa perinteistä virtuaalikonepohjaista virtualisointia pilvessä. Käyttäjä saa käyttöönsä oman virtuaalipalvelimen.
  * **Azure Container Instances / Azure Kubernetes Service (AKS):** Tarjoaa konttiteknologiaa pilvessä, mahdollistaen Docker-konttien ja orkestroinnin ilman, että tarvitsee hallita omia palvelimia.

---

## **3. Vertailu**

| Ratkaisu                            | Taso                 | Eristys                        | Hyödyt                                                | Esimerkki                |
| ----------------------------------- | -------------------- | ------------------------------ | ----------------------------------------------------- | ------------------------ |
| **VirtualBox**                      | Kone / OS            | Täysi (oma käyttöjärjestelmä)  | Voidaan ajaa eri käyttöjärjestelmiä, hyvä testaukseen | VirtualBox               |
| **Docker**                          | Sovellus / Container | Kevyt (sama ydin jaettu)       | Nopea, kevyt, siirrettävä                             | Docker                   |
| **Azure Virtual Machines**          | Pilvi / VM           | Täysi (virtuaalikone pilvessä) | Skaalautuva, valmis infra                             | Azure VMs                |
| **Azure Container Tech (AKS, ACI)** | Pilvi / Container    | Kevyt (kontit pilvessä)        | Nopea käyttöönotto, integroitu pilvipalveluihin       | Azure Kubernetes Service |

---

👉 Näin saadaan kokonaiskuva: **Sandboxing** on ajatus turvallisesta eristämisestä, ja sen toteutus voi tapahtua koneella (VirtualBox), konttina (Docker), tai pilvessä (Azure VMs, Azure konttiteknologia).

---

# **🧩 Sandboxing ohjelmoinnissa ja ohjelmistokehityksessä**

## **1. Testaus ja kehitysympäristöt**

* **Sandbox** on tyypillinen termi ohjelmistokehityksessä kuvaamaan erillistä ympäristöä, jossa uutta koodia voidaan ajaa **ilman riskiä rikkoa tuotantoa**.
* Esim. web-palveluissa on usein kolme ympäristöä:

  * **Dev** (kehitysympäristö, nopeaa kokeilua varten)
  * **Test/Staging** (sandbox tuotantoa jäljittelevä ympäristö, jossa kokeillaan uusia ominaisuuksia)
  * **Prod** (tuotantoympäristö, oikeat käyttäjät)

👉 Sandboxing tukee **Continuous Integration / Continuous Deployment (CI/CD)** -mallia, koska kehittäjät voivat kokeilla koodiaan turvallisesti ennen julkaisua.

---

## **2. Ohjelmakoodin ajaminen sandboxissa**

* Joissain kielissä ja alustoissa voidaan ajaa koodia suoraan **rajoitetussa sandboxissa**.

  * **Java Virtual Machine (JVM):** Java Appletit ajettiin alun perin selaimessa sandboxissa.
  * **.NET CLR (Common Language Runtime):** Mahdollistaa koodin ajon hallitussa ympäristössä.
  * **Python / Node.js -sandboxit:** Käytetään esim. verkkopalveluissa, joissa käyttäjän syöttämää koodia pitää ajaa turvallisesti.

👉 Tärkeä, jos halutaan antaa mahdollisuus suorittaa pieniä koodinpätkiä ilman, että ne pääsevät käsiksi koko järjestelmään.

---

## **3. Sandbox ja automaattinen testaus**

* **Unit testit ja integraatiotestit** voidaan ajaa sandboxissa, jolloin:

  * Testit eivät muuta tuotantodataa.
  * Väärät muutokset voidaan resetoida nopeasti.
* **Tietokantatestaus:** Käytetään "sandbox-tietokantaa", joka on erillinen kopio tuotannosta.

---

## **4. Sandbox ja oppimisympäristöt**

* Monissa opetusalustoissa (esim. repl.it, GitHub Codespaces, Azure Lab Services) koodi ajetaan sandboxissa.
* Tämä mahdollistaa sen, että voidaan kokeilla ohjelmointia ilman, että koneelle tarvitsee asentaa mitään riskialtista.

---

## **5. Yhteys virtualisointiin**

* **VirtualBox sandbox:** Voidaan luoda erillinen testiympäristö, jossa ajetaan uutta ohjelmaa. Jos ohjelma kaatuu → ei haittaa, koska se ei riko isäntäkonetta.
* **Docker sandbox:** Kehittäjät voivat ajaa sovellusta kontissa, joka jäljittelee tuotantoympäristöä. Näin varmistetaan, että ohjelma toimii samalla tavalla kehityksessä ja tuotannossa.
* **Azure sandbox:** Pilvipalveluissa kehittäjille tarjotaan usein **Azure Sandbox** -resursseja, joissa he voivat testata ilman kustannuksia.

---

## **6. Esimerkkiskenaario ohjelmoinnista**

* Kehittäjä tekee uuden API\:n käyttäen **Node.js + Docker**.
* Hän ajaa koodinsa **sandbox-docker-kontissa**, jossa on myös testitietokanta.
* CI/CD putki (esim. GitHub Actions) ajaa automaattisesti testit kontissa.
* Kun kaikki toimii → koodi voidaan julkaista **Azure Virtual Machineen** tai **Azure Kubernetes Serviceen**.

---

## **🎯 Yhteenveto**

* Sandboxing = **turvallinen eristys**.
* Ohjelmoinnissa se tarkoittaa:

  * Kehitysympäristöjä (Dev/Test/Prod).
  * Koodin ajamista rajatussa ympäristössä.
  * Automaattisen testauksen ja CI/CD\:n luotettavuutta.
  * Virtualisointi- ja konttiteknologioiden hyödyntämistä.

---

# **Debian-testikone Python-skriptin testausta varten**

## **🎯 Tarkoitus ja tavoite**

* **Tarkoitus:** luoda turvallinen, toistettava “sandbox”, jossa Python-koodi voidaan asentaa, ajaa ja rikkoa ilman vaikutusta isäntäkoneeseen.
* **Tavoitteet:**

  1. vakioitu testialusta (Debian),
  2. Python-ympäristö,
  3. helppo etäkehitys VS Code + SSH,
  4. nopea palautus **snapshotilla**.

---

## **🧱 Ympäristön arkkitehtuuri lyhyesti**

* **Host:** oma läppäri/työasema (Windows/macOS/Linux) + VirtualBox.
* **Guest/VM:** Debian, OpenSSH server, Python.
* **Verkko:** Bridged.
* **Kehitys:** VS Code **Remote – SSH** -liitännäinen.

---

## **🔧 Esivaatimukset**

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Debian](https://www.debian.org/distrib/)
* [VS Code](https://code.visualstudio.com/) + **Remote – SSH** -laajennus

---

## **🚀 Käyttöönotto: VM pystyyn**

1. **Luo VM:** New → Name: `py-sandbox-debian` → Type: Linux → Version: 'Debian' (64-bit).
2. **Resurssit:** Memory 4 GB, CPU 2–4 vCPU (riippuu koneesta).
3. **Levy:** 20 GB VDI, dynamically allocated.
4. **ISO:** Storage → Controller IDE → liitä Debian ISO.
5. **Verkko:** Network → Adapter 1 = **Bridged adapter**
6. Käynnistä VM ja asenna Debian (valitse asennuksessa **OpenSSH server**).

---

## **🛡️ Peruskonfiguraatio (guest/VM)**

Kirjaudu sisään VM\:lle root-käyttäjänä (konsoli).

```bash
# Asennetaan sudo (HUOM! käyttäjänimi on se, joka asennuksessa määriteltiin)
apt update && apt -y upgrade
apt install sudo
usermod -aG sudo käyttäjänimi

# Varmista SSH-palvelu
systemctl status ssh || systemctl enable --now ssh

# Kirjaudutaan SSH-yhteydellä järjestelmään
# Vaihe 1: Tarkista Debian-koneen IP-osoite
ip a

# Vaihe 2: Avaa isäntäkäyttöjärjestelmästä komentotulkki (Esim: Powershell)
# Vaihe 3: Annan komento
ssh käyttäjänimi@IP-osoite

# Esimerkkinä
ssh linuxadmin@192.168.1.124
```

**Snapshot ennen testausta:**
VirtualBox → VM → **Take Snapshot** → “base-clean”.

---

## **🔗 Kytkentä VS Codeen (Remote – SSH)**

**Isäntäkoneelle:**

1. Asenna **Remote – SSH** -laajennus.
2. VS Code: **> Remote-SSH: Connect to the host...  →  enter user@host → enter password**.
3. Kun yhteys auki, avaa VM\:n kansio (`/home/käyttäjänimi`)

---

## **🐍 Python-testiympäristö**

Luo yksinkertainen Python-skripti VS Codella ja aja se VM\:llä

Luo kansio: **`app`**

```bash
# VM:llä (Esim. VS Coden terminaalissa)
mkdir -p ~/app && cd ~/app
```

Luo tiedosto (Esim. VS Codella): **`main.py`**

```python
def add(a, b):
    return a + b

if __name__ == "__main__":
    print("Hello from VM! 2 + 3 =", add(2, 3))
```

**Aja:**

```bash
# VM:llä (Esim. VS Coden terminaalissa)
python3 main.py
# odotettu tuloste:
# Hello from VM! 2 + 3 = 5
```

---

## **🔁 Snapshot-työskentely**

* **Testauksen jälkeen:** Take Snapshot “first-test-completed”.
* Jos ympäristö sotkeentuu: **Restore Snapshot** takaisin “base-clean”.

---

## **✅ Tarkistuslista**

* [ ] VM pystyssä, päivitykset ajettu
* [ ] OpenSSH server päällä, **SSH toimii** (VS Code Remote – SSH)
* [ ] Snapshot “base-clean” tallessa
* [ ] Visual Studio Code yhdistetty SSH-yhteydellä
* [ ] Snapshot “first-test-completed” tallessa

---