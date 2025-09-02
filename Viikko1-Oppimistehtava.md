# **Viikko 1: GitHub tutuksi**

## **📌 Alkutoimet**

### **Tehtävä 0 (Tästä voi olla osa jo tehtynä)**

**Vaiheet**
1. Varmista, että sinulla on **oppilaitoksen sähköposti** (esim. *@centria.fi*).
2. Asenna **Git** (Windows: Git for Windows, macOS: Xcode Command Line Tools tai Homebrew `git`, Linux: `apt install git`).
3. Asenna **Visual Studio Code** (tai päivitä uusin versio).
4. Aktivoi **2-vaiheinen todennus (2FA)** puhelinsovelluksella (esim. Microsoft Authenticator).

---

### **Tehtävä 1 — GitHub-tilin perustaminen ja koventaminen**

**Vaiheet**
1. Luo **GitHub-tili** oppilaitoksen sähköpostilla (suositus: selkeä käyttäjänimi).
2. Ota käyttöön **2FA** GitHubissa (Asetukset → Password and authentication).
3. Aseta käyttäjätiedot koneellesi (`git bash komentoriviltä`):
   * `git config --global user.name "Etunimi Sukunimi"`
   * `git config --global user.email "koulusähköpostisi"`

---

### **Tehtävä 2 — GitHub Education / Student Developer Pack -hakemus**

**Vaiheet**
1. Siirry **GitHub Education** -sivulle ja valitse *Student* → Apply.
2. Käytä **oppilaitoksen sähköpostia** ja täytä vaadittavat kohdat (opiskelutodistus/linkki oppilaitokseen tmv. jos pyydetään).
3. Lähetä hakemus.
4. **Jos Approved:** varmista, että Student Developer Pack näkyy tililläsi.
   **Jos Pending/Rejected:** dokumentoi tilanne ja korjaavat toimet (esim. lisää todistus, odota käsittely).

---

## **📌 Tehtävän vaiheet**

1. **Luo uusi GitHub-repositorio selaimella**

   * Mene GitHubiin ja kirjaudu sisään.
   * Paina **New repository**.
   * Anna repolle sopiva nimi.
   * Valitse **Private**.
   * Luo repositorio.

2. **Kloonaa repositorio Visual Studio Codeen**

   * Avaa repositorion etusivu GitHubissa.
   * Kopioi **HTTPS-osoite** (muotoa `https://github.com/kayttaja/repo.git`).
   * Avaa **Visual Studio Code**.
   * Valitse **Clone Repository** ja liitä kopioitu osoite.
   * Valitse kansio koneeltasi, johon repo kloonataan.

3. **Tarkista että kloonaus onnistui**

   * VSC avaa repokansion automaattisesti.
   * VSC\:n vasemmasta laidasta näet versionhallinnan näkymän (Source Control).
   * Tee pieni testitiedosto (esim. `README.md`) ja tee ensimmäinen commit + push.

> [!NOTE]  
> **Palauta yksi (1) kuvakaappaus, josta näkyy**  
> **1. selaimelta, että repo on private**
> **2. Visual Studio Codelta, commit + push meni läpi** 
