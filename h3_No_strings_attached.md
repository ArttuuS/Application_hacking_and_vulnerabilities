# h2 No strings attached

Ympäristö tehtävien ratkaisussa: Acer Aspire A515-52, Windows 10, Oracle VirtualBox jolle asennettu Debian 12 Bookworm.

## a)

Tätä tehtävää lähdin tekemään täysin tehtävänannon mukaan. "Strings"-ohjelmasta luin hyvän artikkelin How-To-Geekin-sivuilta, jonka avulla sain hieman käsitystä sen toiminnasta. Artikkeli löytyy lähdeviitteistä ensimmäisenä.

Ohjelman oikea salasana sekä myös flägi löytyy helposti käyttäen strings passtr komentoa. 

![strings](https://github.com/user-attachments/assets/deb2178d-17c6-4a58-a02f-6b106a194b62)

![strings2](https://github.com/user-attachments/assets/dde89cf2-58eb-4a6a-9bfb-2d8a38cd9029)

## b)

B-tehtävää lähdin alustamaan lukemalla c-ohjelmointikielen obfuskoinnista eri sivustoilta. Päädyin toteutuksessani erittäin yksinkertaiseen ratkaisuun, mikä toteuttaa sen, että salasana ei ole sellaisenaan nähtävissä juuri esimerkiksi Strings-ohjelmalla. Käytän XOR encryptonia, mikä tekee sen, että salasana on strings-ohjelmaa käytettäessä eri muodossa. XOR encryption ei kuitenkaan ole missään nimessä riitä herkemmän tiedon suojaamiseen, sillä se on suhteellisen helppo purkaa. Lisäämällä tähän ratkaisuun esimerkiksi LLVM obfuscatorin, saisi turvallisuudesta vielä paremman. Malliratkaisuun käytin Stack Overflow-foorumilla esiteltyä yksinkertaista ratkaisua, jota muokkasin käyttötarkoitukseeni ChatGPT:n avulla. 

![Näyttökuva 2024-11-10 205343](https://github.com/user-attachments/assets/3b7c1606-5166-4122-b82f-35836db55954)

(Yksinkertainen XOR implementaatio, Stack Overflow 2011)

Aluksi loin yksinkertaisen sovelluksen, joka salaa "sala-hakkeri-321" merkkijonon käyttämällä XOR-salausta, jossa jokainen merkki yhdistetään salausavaimen arvoon bittitasolla. 

![kuva (8)](https://github.com/user-attachments/assets/0e59963c-15ea-4a6f-8d98-7267dc20b89d)

Käännetään, ja käynnistetään sovellus. Sovellus antaa "encryptatun" salasanan, joka kopioidaan.

![kuva (9)](https://github.com/user-attachments/assets/2da30ead-4e89-4e4e-bec5-871245f92907)


Sitten muokkaamaan itse pääohjelmaa. Muokatussa pääohjelmassa on sama encrypt funktio kuin salasanan encryptointi ohjelmassa. Käyttämällä samaa funktiota uudelleen, saadaan encryptattu salasana palautettua alkuperäiseen muotoon. 

Encryptattava salasana on kopioitu aiemman ohjelman syötteestä. Tämä on siis sala-hakkeri-321, mutta ei suoraan ihmisen luettavissa.

Muokkaamattomassa versioissa verrattiin käyttäjän syötettä suoraan "sala-hakkeri-321"-merkkijonoon, mutta nyt salasana puretaan ensin encrypt()-funktiolla ja sen jälkeen tehdään vertailu. Merkkijonoa "sala-hakkeri-321" ei siis löydy suoraan lähdekoodista laisinkaan.  

![kuva (10)](https://github.com/user-attachments/assets/4ef16540-561e-47bd-bdc2-bff38e6478d1)

Tässä vielä testaus Strings-komennolla. Voidaan havaita, että salasanaa ei löydy sellaisenaan listasta.

![kuva (11)](https://github.com/user-attachments/assets/722da70b-6a17-4efc-a76d-055f9a7b6845)

## c)

Lähdin tekemään tätä tehtävää samalla tavalla kuin a) tehtävää, eli käytin Strings komentoa ohjelmaan. Ensimmäinen ajatukseni oli, että salasana on esimerkiksi encryptattu eri muotoon. Stringsin syötteestä löytyi "salasana" "piilos-An". Testasin kyseistä salasanaa, mutta se ei ollut ratkaisu. 

Tutkiessani stringsin syötettä enemmän huomasin, että tiedosto on pakattu käyttäen UPX:ää. 
UPX on ilmainen, turvallinen, kannettava, laajennettava ja tehokas suoritettava pakkaaja useille suoritettaville formaateille (UPX 2024).

![kuva (12)](https://github.com/user-attachments/assets/ae9f757c-ef63-4a65-b07f-b444d18f71b7)

Asensin virtuaalikoneeseeni UPX:än ja googletin sen eri komentoja. Löysin komennon "upx -d", jolla tiedostoja voidaan purkaa. Suorittamalla komennon "upx -d packd" yksi tiedosto tuli puretuksi.

![kuva (13)](https://github.com/user-attachments/assets/e3350f18-20cc-43b3-8025-ac324988e4ca)

Tämän jälkeen käytin Strings-komentoa uudelleen ja salasana ja fläg tuli näkyviin oikeassa muodossa.

![kuva (14)](https://github.com/user-attachments/assets/2ed40b60-b965-4692-bece-9de1bf9777f1)

![kuva (15)](https://github.com/user-attachments/assets/fb129e84-364d-4fee-858f-98a724387b5b)

## d)


## Lähteet

Mckay, D. 9.7.2019. How to Use the strings Command on Linux. Luettavissa: https://www.howtogeek.com/427805/how-to-use-the-strings-command-on-linux/. Luettu 7.11.2024.

Clang 2024. Getting Started: Building and Running Clang. Luettavissa: https://clang.llvm.org/get_started.html. Luettu 7.11.2024.

Digital.ai 2024. How to Obfuscate C Code. Luettavissa: https://digital.ai/catalyst-blog/how-to-obfuscate-c-code/. Luettu 7.11.2024.

Stack Overflow 2011. Simply encrypt a string in C. Luettavissa: https://stackoverflow.com/questions/7622617/simply-encrypt-a-string-in-c. Luettu 10.11.2024.

https://upx.github.io/

https://linux.die.net/man/1/upx
