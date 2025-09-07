> [!NOTE]
> Materiaali on luotu ChatGPT:n ja Copilotin avulla.

# Viikko 2: HTML-sivun julkaisu GitHub Pagesiin Actionsilla

## 🎯 Tavoite
- Luo ja kloonaa GitHub-repo **HTTPS**-yhteydellä Visual Studio Codeen  
- Ota käyttöön **Live Server** -laajennus ja katso HTML-sivua paikallisesti  
- Tee commit (VS Code / Git Bash / GitHub Desktop)  
- Julkaise sivu GitHub Pagesiin **GitHub Actionsin** avulla  
- Muuta sivua ja seuraa, miten muutos etenee  

---

## 📝 Vaihe 1: Luo GitHub-repo
1. Mene GitHubiin → **New repository**.
2. Nimeä valitsemallasi nimellä.
3. Valitse **Public**.
4. Valitse **Add a README file**.
5. Paina **Create repository**.

---

## 📝 Vaihe 2: Kloonaa repo HTTPS\:llä Visual Studio Codeen

1. Reposivulla → **Code** → **HTTPS** URL (muotoa `https://github.com/<käyttäjänimi>/<repo>.git`).
2. VS Codessa → **View → Command Palette… → Git: Clone** → liitä URL → valitse kansio.
3. Kun kysyy → avaa projekti VS Codessa.

---

## 📝 Vaihe 3: Asenna Live Server -laajennus

1. VS Codessa → vasemmasta sivupalkista **Extensions** (kuutio-ikoni).
2. Hae **Live Preview** (Julkaisija: *Microsoft*).
3. Klikkaa **Install**.

---

## 📝 Vaihe 4: Luo `index.html`
Projektin juureen tiedosto:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Hello Pages via Actions</title>
</head>
<body>
  <main>
    <h1>Hello GitHub Pages!</h1>
    <p>This page is deployed automatically with GitHub Actions.</p>
  </main>
</body>
</html>
``` 

## 📝 Vaihe 5: Avaa sivu selaimessa paikallisesti

1. Avaa `index.html` VS Codessa.
2. Klikkaa oikealla → **Open with Live Server**.
3. Selain avautuu osoitteeseen esim. `http://127.0.0.1:5500/index.html`.

   * Näet sivun heti.
   * Muuta tekstiä → tallenna → selain päivittyy automaattisesti.

---

## 📝 Vaihe 6: Tee commit ja push

### Vaihtoehto A: Commit VS Codella

1. Vasemman reunan **Source Control** -välilehti (haaroja muistuttava ikoni).
2. Kirjoita commit-viesti (`Add index.html`).
3. Paina ✔ **Commit**.
4. Paina **Sync Changes** tai **Push** → tiedosto lähtee GitHubiin.

### Vaihtoehto B: Commit Git Bashilla

```bash
git add index.html
git commit -m "Add index.html"
git push origin main
```

### Vaihtoehto C: Commit GitHub Desktopilla

1. Avaa GitHub Desktop → valitse kloonattu repo.
2. Näet muutoksen listassa (index.html).
3. Kirjoita commit-viesti → **Commit to main**.
4. Paina **Push origin**.

---

## 📝 Vaihe 7: Lisää GitHub Actions -workflow julkaisuun

Luo kansio `.github/workflows/` ja tiedosto `pages.yml`:

```yaml
name: Deploy static site to GitHub Pages

on:
  push:
    branches: [ "main" ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: "."

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

Commit & push (valitse oma tapa: VS Code, Git Bash tai GitHub Desktop).

---

## 📝 Vaihe 8: Aktivoi GitHub Pages

1. GitHub repo → **Settings → Pages**.
2. Tarkista, että **Build and deployment** = *GitHub Actions*.
3. Kun workflow on ajettu onnistuneesti → sivu näkyy osoitteessa:

   ```
   https://<käyttäjänimi>.github.io/<repo>/
   ```

---

## 📝 Vaihe 9: Testaa julkaisu

* Mene **Actions**-välilehdelle → varmista vihreä check.
* Avaa URL → näet saman sivun kuin Live Serverissä.

---

## 📝 Vaihe 10: Tee muutos ja seuraa sen etenemistä

1. Avaa `index.html` uudestaan.
2. Muuta esimerkiksi `<h1>`-rivi:

   ```html
   <h1>Hello GitHub Pages! (Updated)</h1>
   ```
3. Katso muutos **Live Serverissä** (päivittyy heti selaimeen).
4. Tee commit ja push (valitse taas haluamasi tapa).
5. Tarkkaile GitHubin **Actions**-välilehteä → uusi workflow käynnistyy.
6. Kun se on vihreä → päivitä GitHub Pages -URL selaimessa → muutos näkyy myös julkisessa versiossa.

---

## ✅ Palautus

1. GitHub-repon linkki.
2. Pages-julkaisun URL.
3. Kuvakaappaukset:
   * Live Server -näkymä
   * Actionsin onnistunut ajo.

---

## **👉 Bonus (Ei tarvitse palauttaa)**

1. Testaa tiedoston lisääminen selaimella → Miten saat tiedoston näkymään omalla koneella?
2. Päivitä (muuta sisältöä) tiedostoa selaimella ja Visual Studio Codella → Mitä seuraa commit+push jälkeen?
3. Testaa tiedoston poistaminen poistaminen selaimella + VSC commit+push → Mitä seuraa?
4. Testaa tiedoston poistaminen poistaminen VSC:llä + commit+push → Mitä seuraa? 

**Leiki Gitin kanssa!**

