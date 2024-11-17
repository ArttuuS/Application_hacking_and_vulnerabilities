## h4 Kääntöpaikka

Ympäristö tehtävien ratkaisussa: Acer Aspire A515-52, Windows 10, Oracle VirtualBox jolle asennettu Debian 12 Bookworm, Java 17, Ghidra 11.1.2.

# x)

* Videossa ladataan sovellus, jonka flägi yritetään selvittää.

* Ennen ghidran käyttöä on hyvä käyttää esimekriksi ltrace ja strace ohjelmia. Ltrace seuraa ohjelman kutsumia kirjasto ja järjestelmäfunktioita. Strace seuraa ohjelman suorittamia järjestelmäkutsuja.

* Myös objdumpia käytetään videolla. Se purkaa käännetyn binäärin ja näyttää sen sisältöä.

* Videossa asennetaan jdk versio 11 ja ghidra.

* Ohjelma avataan gidralla ja aluksi videolla tarkistellaan "defined stringsejä"

* Funktioita ja muita ohjelman osia voi uudelleen nimetä, jolloin helppolukuisuus paranee.

* Flägi selvitetään kopioimalla ehtolauseesta hex-luku, joka muutetaan desimaali luvuksi pythonin avulla.

# a)

Java 17 ja Ghidra 11.1.2 asennettu:

![Näyttökuva 2024-11-17 115149](https://github.com/user-attachments/assets/eda5a62d-b079-4ce3-ade9-9b52d73bd4a8)

![Näyttökuva 2024-11-17 115501](https://github.com/user-attachments/assets/ca1ea726-1007-4eee-8b26-f53579523141)

# b)

Avasin packd-ohjelman Ghidrassa. Defined strings muistuttu siitä, että osa tiedostoista on pakattu, joten purin tiedoston ennen varsinaista tutkiskelua.

![Näyttökuva 2024-11-17 122606](https://github.com/user-attachments/assets/b5f4d676-3a79-456d-9716-f4ed3fe1a2bf)

![Näyttökuva 2024-11-17 122720](https://github.com/user-attachments/assets/9481780c-a25f-4c1d-9793-6941aa478d90)

Tein kolme muutosta muuttujien nimiin, jotka tekevät binääristä helppolukuisemman:

  * undefined 8 --> int
  * iVar1 --> password_match
  * local_28 --> user_input

Oikea salasana löytyy helposti, kun tiedosto on purettu.

Alkuperäinen:

![Näyttökuva 2024-11-17 124544](https://github.com/user-attachments/assets/09af1a94-8604-40c3-a10a-6257d8f3cf06)

Muokattu:

![Näyttökuva 2024-11-17 124631](https://github.com/user-attachments/assets/31527634-6ae7-4559-8bf1-b4ff889d82ba)

![Näyttökuva 2024-11-17 124735](https://github.com/user-attachments/assets/6b87ea0e-3d2c-4587-8315-846d8d6ad4ae)

# c)

Avasin aluksi ohjelman Ghidrassa. Viime tunti antoi hyvät lähtökohdat tämän tehtävän toteuttamiseen. Löysin samoin kaksi hyvää artikkelia tämän kaltaisen tehtävän tekemisestä (löytyy liitteistä). 

Decompilesta ehtolausetta painaessa voidaan tutkia binääriä tarkemmin. Binääristä pystyy paikantamaan "ehdollisen hypyn" (conditional jump), joka määrittelee milloin "hyppy tehdään". Tällä hetkellä asetus on JNZ, eli "jump if not zero". Tämä tulee tehtävän ratkaisemiseksi muuttaa --> JZ, eli "jump if zero". Tällöin ohjelman logiikka kääntyy päinvastaiseksi.

Muutos tehdään "Patch Instruction"- toiminnolla. Tämän jälkeen ohjelma exportataan. Ohjelmaa ei pystynyt ainakaan minun tapauksessa suoraan käynnistämään vaan komento "chmod +x" tuli syöttää. Tämä tekee ohjelmasta suoritettavan.

![Näyttökuva 2024-11-17 194850](https://github.com/user-attachments/assets/9f3713a6-9bc5-4dfd-8a26-89cb7b4ce74a)

![Näyttökuva 2024-11-17 204233](https://github.com/user-attachments/assets/3e83d980-92d9-42fc-808e-f3711a460e9a)

![Näyttökuva 2024-11-17 204300](https://github.com/user-attachments/assets/574462b3-2aa5-446a-8928-4b8051f44e14)

![Näyttökuva 2024-11-17 203957](https://github.com/user-attachments/assets/f586a87a-bc36-4f59-8268-416c4476cf6f)

# d)

Latasin tehtävät Githubista ja purin kansion. Make-komennolla koin tarvittavat kolme ohjelmaa.

![Näyttökuva 2024-11-17 205310](https://github.com/user-attachments/assets/88bd9b1a-ff9c-4e3b-9d72-0dd41675ca48)

# e)

Aloitin tehtävän avaamalla tehtävän Ghidrassa. Löysin oikean salasanan nopeasti Defined Stringsin kautta. Olin kuitenkin aluksi erittäin hämilläni, että miten salasana syötetään ohjelmaan, joten aloin taas muokkaamaan JNZ muotoa JZ:aksi. Tällä kertaa tässä ratkaisussa tuli ongelmia ja päädyinkin aloittamaan puhtaalta pöydältä. Hieman binääriä enemmän tutkiskellessa tajusin, että salasana tulee laittaa heti suorituskomennon perään. Salasana oli siis password1.

![Näyttökuva 2024-11-17 205759](https://github.com/user-attachments/assets/e3e71cde-2cfc-469c-b567-078c5e0eca23)

![Näyttökuva 2024-11-17 212201](https://github.com/user-attachments/assets/e9091e8d-7428-4810-ad57-70288f7d0cfc)

# e)

Tätä tehtävää lähdin tekemään samalla tapaa kuin edellistä. Defined stringsin ja decompile viewin kautta salasana löytyi nopeasti. Tällä kertaa ongelmia tuotti salasanan syöttäminen. Syötetty salasana sekottui linux komentona. Löysin Redditistä hyvän keskustelun aiheesta (screenshot ja lähde) ja ratkaisu oli laittaa salasana '' väliin.

![Näyttökuva 2024-11-17 213143](https://github.com/user-attachments/assets/2ae01972-707d-49c3-9a0a-0645736ac54d)

![Näyttökuva 2024-11-17 214230](https://github.com/user-attachments/assets/ec9f3cdc-9033-45a0-9d40-a890433e2187)

(Geirha, Reddit 2020)

![Näyttökuva 2024-11-17 214212](https://github.com/user-attachments/assets/408c5dd2-13eb-4039-afa0-7085012175e5)

# f)

Itse en ole koskaan C:tä koodannut, niin ohjelman muuttujien nimeäminen ja logiikan ymmärtäminen oli vaikeaa.

Vastauksen selvittäminen myös todella vaikealta ja päädyin kokeilemaan Teron näyttämiä kikkoja, kuten tyhjän testaamista. ""-toimi tässä tehtävässä, mutta vastaus on toki vajaa, sillä itse salasana ei tule selville. 

![Näyttökuva 2024-11-17 215645](https://github.com/user-attachments/assets/bc4c7e28-d3ba-4963-89c3-894b114e8807)

Muuttujien nimeämiseen kysyin apua chatgpt:ltä, ja tein nimeämisen sen ohjeiden mukaisesti.

Alkuperäinen:

![Näyttökuva 2024-11-17 220156](https://github.com/user-attachments/assets/59cade8b-2bae-498b-a8b0-5f61a2c79301)

Muokattu:

![Näyttökuva 2024-11-17 221128](https://github.com/user-attachments/assets/f22d9dbb-bda9-4d80-8497-4fa477547957)

Kävin uteliaisuudesta katsomassa lähdekoodia ja sieltä löytyikin oikea vastaus.

![Näyttökuva 2024-11-17 221704](https://github.com/user-attachments/assets/9d9f4525-b962-4bb4-96fd-88dd0832e050)

# Lähteet

Reddit 2020. Luettavissa: https://www.reddit.com/r/bash/comments/cl54to/not_sure_why_mac_is_saying_bash_event_not_found/?rdt=58517. Luettu: 17.11.2024.

Jorian Woltjer 2022. Introduction to Reverse Engineering (with Ghidra). Luettavissa: https://jorianwoltjer.com/blog/p/hacking/introduction-to-reverse-engineering-with-ghidra. Luettu 17.11.2024.

Jean-Michel Amblat 2019. First steps with Ghidra: crackme01. Luettavissa: https://medium.com/@jeanmichel.amblat/first-steps-with-ghidra-crackme01-319827a2e80b. Luettu 17.11.2024.
