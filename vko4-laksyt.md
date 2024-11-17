## h4 Kääntöpaikka
### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
Hammond 2022: Ghidra for Reverse Engineering (PicoCTF 2022 #42 'bbbloat') (Video, noin 20 min)

### a) Asenna Ghidra.
  - Ghidran asennus, sekä käynnistys onnistui seuraavilla komennoilla
    ```
        sudo apt-get install openjdk-17-jdk
        wget https://github.com/NationalSecurityAgency/ghidra/releases/download/Ghidra_11.1.2_build/ghidra_11.1.2_PUBLIC_20240709.zip
        unzip ghidra_11.1.2_PUBLIC_20240709.zip
        ./ghidraRun
    ```
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
### b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia. 
- Tehtävä aloitettiin purkamalla packd tiedosto käyttäen upx ohjelmaa.
  
<img src="https://i.imgur.com/6TG8pD5.png" alt="Alternate image text" width="400"/>

- Seuraavaksi avasimme tiedoston ghidraan, käyttämällä import file toimintoa.
<img src="https://i.imgur.com/O27XQ2s.png" alt="Alternate image text" width="400"/>

- Tämän jälkeen tupla klikkasimme tiedoston auki, jonka jälkeen haimme sieltä main function.
- 
<img src="https://i.imgur.com/73fkLNv.png" alt="Alternate image text" width="400"/>
- Tupla klikkaamalla functiota se aukesi Decompile ikkunaan, josta löydämme salasanan "piilos-AnAnAs"
- Näemme myös Lipun FLAG{Tero-...............}
<img src="https://i.imgur.com/zjDlhBj.png" alt="Alternate image text" width="400"/>
### c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman alkuperäistä lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii. ezbin-challenges.zip

<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>

### d) Nora CrackMe: Käännä binääreiksi Tindall 2023: NoraCodes / crackmes. Lue README.md: älä katso lähdekoodeja, ellet tarvitse niitä apupyöriksi. Näissä tehtävissä binäärejä käänteismallinnetaan. Binäärejä ei muokata, koska muutenhan jokaisen tehtävän ratkaisu olisi vaihtaa palautusarvoksi "return 0".

<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
### e) Nora crackme01. Ratkaise binääri.
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
### e) Nora crackme01e. Ratkaise binääri.

<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
### f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.

<img src="" alt="Alternate image text" width="400"/>
<img src="" alt="Alternate image text" width="400"/>
