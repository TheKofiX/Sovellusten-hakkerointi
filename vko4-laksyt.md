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
### b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia. 
- Tehtävä aloitettiin purkamalla packd tiedosto käyttäen upx ohjelmaa.
  
<img src="https://i.imgur.com/6TG8pD5.png" alt="Alternate image text" width="400"/>

- Seuraavaksi avasimme tiedoston ghidraan, käyttämällä import file toimintoa.
<img src="https://i.imgur.com/O27XQ2s.png" alt="Alternate image text" width="400"/>

- Tämän jälkeen tuplaklikkasimme tiedoston auki, jonka jälkeen etsimme sieltä main funktion.
  
<img src="https://i.imgur.com/73fkLNv.png" alt="Alternate image text" width="800"/>

- Tuplaklikkaamalla funktiota se aukesi Decompile ikkunaan, josta löydämme salasanan "piilos-AnAnAs"
- Näemme myös Lipun FLAG{Tero-...............}
  
<img src="https://i.imgur.com/zjDlhBj.png" alt="Alternate image text" width="400"/>

### c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman alkuperäistä lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii. 

- En ollut ennen kyseistä tehtävää tietoinen assemblystä oikeastaan ollenkaan. En kuitenkaan halunnut chatgpt:ltä suoraa vastausta, vaan oppia asian itse, joten kysyin kuinka assemblyssä voitaisiin saavuttaa se, että ohjelma hyväksyy kaikki salasanat paitsi oikean. Se kertoi minulle JNZ ja JZ käskyistä.
- Tämä toi minut seuraaviin lähteisiin:<br> [Assembly Language Programming Tutorial - 40 - Conditional Jumps](https://www.youtube.com/watch?v=CCG1rVRgdJ0) <br> [Conditionals and jump instructions](https://www.infosecinstitute.com/resources/secure-coding/conditionals-and-jump-instructions/) 
- JNZ ja JZ, ymmärrykseni mukaan siis kertovat ohjelmalle hypätä tiettyyn kohtaan tietyn komennon tapahtuessa. Esim. Salasana oikein --> Hyppää ohjelman riville x
- Näin muuttamalla kyseisen käskyn toisin päin saimme halutun tuloksen.
  <br>
- Alkuperäinen alla.
  
<img src="https://i.imgur.com/OpWhQLy.png" alt="Alternate image text" width="600"/>

- Muutettu JZ käsky alla.
  
<img src="https://i.imgur.com/B8KvTaW.png" alt="Alternate image text" width="600"/>

- Alla vielä lopputulos toiminnasta, eli oikea salasana ei toimi, muut toimivat.
  
<img src="https://i.imgur.com/dzFY7HE.png" alt="Alternate image text" width="400"/>

### d) Nora CrackMe: Käännä binääreiksi Tindall 2023: NoraCodes / crackmes. Lue README.md: älä katso lähdekoodeja, ellet tarvitse niitä apupyöriksi. Näissä tehtävissä binäärejä käänteismallinnetaan. Binäärejä ei muokata, koska muutenhan jokaisen tehtävän ratkaisu olisi vaihtaa palautusarvoksi "return 0".

### e) Nora crackme01. Ratkaise binääri.

- Kaikki crackme tehtävät alkoimat rakentamalla ne ajettaviksi tiedostoiksi.

<img src="https://i.imgur.com/kmubm4J.png" alt="Alternate image text" width="400"/>

- Tämän jälkeen tiedosto laitettiin ghidraan, jonka avulla salasana löytyi, joko main funktion alta seuraamalla s_password kohtaa tai katsomalla decompile osasta.
<img src="https://i.imgur.com/XJyCB2F.png" alt="Alternate image text" width="400"/>

- Lopputulos vielä alla.
<img src="https://i.imgur.com/NDm2jRc.png" alt="Alternate image text" width="400"/>

### e) Nora crackme01e. Ratkaise binääri.

- Crackme01e toimi lähes samalla tavalla kuin crackme01.
- Tiedosto rakennettiin, laitettiin ghidraan, sekä haimme main funktion.
  
<img src="https://i.imgur.com/4nkRHE4.png" alt="Alternate image text" width="400"/>

- Ainoa ero oli tehtävää ajaessa, vaadittiin heittomerkit, sillä salasanassa ollut ! aiheutti haittaa.
- Alla alkuun ilman heittomerkkejä.
  
<img src="https://i.imgur.com/5fCXgVS.png" alt="Alternate image text" width="400"/>

- Sitten niiden kanssa.
  
<img src="https://i.imgur.com/1AUATEY.png" alt="Alternate image text" width="400"/>

### f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.

- Crackme02 oli ainoa tehtävä, jota en mielestäni saanut ratkaistua sillä jouduin tukeutumaan ohjelman lähdekoodiin.
- Ymmärsin tehtävän decompile osiosta, että salasanaa muutetaan käyttäen jonkun näköistä looppia, jossa tulosta vähennetään. En kuitenkaan ymmärtänyt kuinka tämä toimii, tai kuinka ratkaisisin asian.
- Näin ollen päädyin avaamaan lähdekoodin, josta löysin oikean vastauksen ja pääsin tutkimaan kuinka tähän päästäisiin.
- Vastaus oli loppujen lopuksi melko simppeli, sillä Ghidran avulla löydetyn salasanan ASCII arvoja miinustettiin vain yhdellä. <br>
- Alla olevassa kuvassa yritin selkeyttää muuttamalla muuttujien nimiä. Tästä myös ilmenee, että salasanaa muutetaan.

<img src="https://i.imgur.com/07YDEyF.png" alt="Alternate image text" width="400"/>
