> [!NOTE]
> Materiaali on luotu ChatGPT:n ja Copilotin avulla.

# Viikko 4: Sandboxing & virtuaaliympäristö testaukseen

## 🎯 Tavoite

* Ymmärtää **sandboxingin idea** ja sen suhde **virtualisointiin** ja **kontteihin**.
* Rakentaa **toistettava Debian-testiympäristö** käyttäen:

  * **VirtualBoxia**, TAI
  * **Azure Virtual Machinea**, TAI
  * **Docker-konttia**.
* Ottaa käyttöön **SSH-yhteys** ja **VS Code Remote – SSH** etäkehitykseen.
* Luoda ja ajaa **yksinkertainen Python-skripti** testiympäristössä.
* Harjoitella **snapshot-työskentelyä** (tai vaihtoehtoisesti Docker image/tag / Azure snapshot).

---

## 🧰 Vaihtoehto 1: Debian-VM VirtualBoxissa

1. Asenna VirtualBox ja lataa Debian ISO.
2. Luo VM (4 GB RAM, 2 CPU, 20 GB levy, Bridged adapter).
3. Asennuksessa valitse **OpenSSH server**.
4. Varmista `ssh` toimii ja ota snapshot “base-clean”.

---

## 🧰 Vaihtoehto 2: Debian/Azure VM

1. Luo Azure-ympäristöön **Virtual Machine**:

   * Image: **Debian 12**
   * Size: B1s tai vastaava (riittää testikäyttöön, huomioi opiskelijatilin resurssirajat).
   * Salli **SSH (portti 22)** palomuurissa.
2. Yhdistä `ssh käyttäjä@VM_PUBLIC_IP`.
3. Ota käyttöön **VS Code Remote – SSH**.
4. Luo Azure-portaalissa **snapshot** VM\:stä (vastaa VirtualBox snapshotia).

---

## 🧰 Vaihtoehto 3: Debian Docker-kontti

1. Asenna Docker (Linuxissa `sudo apt install docker.io`).
2. Käynnistä Debian-kontti:

   ```bash
   docker run -it --name py-sandbox-debian -p 2222:22 debian:latest bash
   ``` 

3. Asenna tarvittavat työkalut konttiin (edellinen komento avaa komentotulkin käynnissä olevasta Docker-kontista):

   ```bash
   apt update && apt -y install python3 openssh-server nano
   ```

4. Asetetaan root-käyttäjälle salasana (edelleen toimitaan Docker-kontin komentoriviltä)
   ```bash
   echo 'root:DockerPassword123' | chpasswd
   ```

5. Muutetaan ssh-ohjelman asetuksia ja käynnistetään (edelleen toimitaan Docker-kontin komentoriviltä)
   ```bash
   mkdir /var/run/sshd
   sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
   /usr/sbin/sshd
   ```

6. Otetaan isäntäkoneesta ssh-yhteys kontin koneeseen
   ```bash
   ssh root@localhost -p 2222
   ```

7. Nyt ssh-yhteys pitäisi olla käytössä ja VSC pystytään yhdistämään.

---

**VS Code Remote-SSH asetukset**

Jos manuaalinen SSH toimii, voit lisätä yhteyden VS Codeen näin:

1. Avaa komentopaletti: `Ctrl+Shift+P`
2. Valitse: `Remote-SSH: Add New SSH Host`
3. Syötä:

```bash
ssh root@localhost -p 2222
```

4. Valitse `config`-tiedosto, johon yhteys tallennetaan (esim. `~/.ssh/config`)
5. Tarkista, että tiedostossa on rivi:

```ssh
Host docker-debian
    HostName localhost
    User root
    Port 2222
```
---

8. (Valinnainen) Luo oma image snapshotiksi:

   ```bash
   docker commit py-sandbox-debian debian-sandbox:v1
   ```

---

## 📚 Tehtävät kaikissa vaihtoehdoissa

1. **SSH ja VS Code**:

   * Yhdistä ympäristöön SSH\:lla.
   * Avaa kansio VS Codessa Remote – SSH\:lla.
2. **Python-skripti**:

   * Luo `~/app/main.py`:

     ```python
     def add(a, b):
         return a + b

     if __name__ == "__main__":
         print("Hello from sandbox!")
         print("2 + 3 =", add(2, 3))
     ```
   * Aja `python3 main.py`.
3. **Snapshot / tallennus**:

   * VirtualBox: Snapshot “first-test-completed”.
   * Azure: Snapshot-portaalista.
   * Docker: `docker commit` uusi versio.

---

## 📤 Palautus
Palauta Itslearningiin **Kuvakaappaus**, josta näkyy:
   * ympäristö (VirtualBox / Azure / Docker),
   * VS Code Remote – SSH,
   * `python3 main.py` tuloste.

---

## ✅ Tarkistuslista

* [ ] Ympäristö pystyssä (VirtualBox / Azure / Docker)
* [ ] SSH-yhteys toimii
* [ ] VS Code Remote – SSH käytössä
* [ ] Python-skripti ajettu
* [ ] Snapshot (tai commit) otettu
* [ ] Palautettu kuvakaappaus