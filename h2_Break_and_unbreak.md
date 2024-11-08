# h2 Break & unbreak

## x)
### OWASP: OWASP Top 10: A01 Broken Access Control & PortSwigger: Access control vulnerabilities and privilege escalation:

-Yksi yleinen tietoturvaongelma on "Broken Access Control" (suom. rikkinäiset käyttöoikeudet), jossa käyttäjä voi päästä käsiksi tietoihin tai toimintoihin, joihin hänellä ei pitäisi olla pääsyä. Tämä voi johtaa luvattomaan tiedon katseluun, muokkaamiseen, poistamiseen tai liiketoimintaprosessien väärinkäyttöön. (OWASP 2021.)

-Yleisiä "Broken Access Control" haavoittuvuuksia on mm. liian laajat käyttöoikeudet, URL-osoitteiden muokkaaminen ja API:n käyttäminen ilman pääsynhallintaa POST-, PUT- ja DELETE-toiminnoille (OWASP 2021).

-"Access control" (pääsynhallinta) on hyödyllistä vain palvelinpuolen koodissa tai palvelimettomassa API:ssa, jossa mahdollinen hyökkääjä ei pysty muokkaamaan pääsynhallintaa (OWASP 2021).

-Turvatoimia, joilla hyökkäyksiä voidaan estää on mm. oletusarvoinen käyttöoikeuksien esto (ei julkisille resursseille), pääsynhallinta mekanismien käyttö yhtenäisesti koko sovellukselle ja pääsynhallinnan epäonnistumisten kirjaaminen ylös. Näitä turvatoimia tulee testata. (OWASP 2021.)

-"Vertical access controls": käyttöoikeusien hallintaa, jolla rajoitetaan herkkiin toimintoihin pääsyä eri käyttäjäryhmille (esim. admin voi muokata ja poistaa minkä tahansa tilin, mutta tavallinen käyttäjä ei). "Horizontal access controls": käyttöoikeuksien hallinan mekanismeja, jotka rajoittavat oikeuksia tietyille käyttäjille (esim. käyttäjä x voi tarkastella oman pankkitilinsä tapahtumia mutta ei käyttäjän y tapahtumia). "Context-dependent access controls": käyttöoikeuksien hallintaa, jonka avulla rajoitetaan toimintoihin pääsyä sovelluksen tilan tai käyttäjän toimenpiteiden perusteella (esim. käyttäjä ei voi muokata ostoskorin sisältöä, maksamisen jälkeen). (PortSwigger 2024.)

### Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf:

-Verkkopalvelimilla on usein salaisia hakemistoja. Näitä voidaan etsiä automaattisesti käyttäen Fuff-työkalua. (Tero Karvinen 2023.)

-Suodattamalla vastauksia, voidaan saavuttaa tarkemmat tulokset (Tero Karvinen 2023).

-Ennen penetraatio työkalujen ja menetelmien käyttöä (sis. fuff), tulee varmistaa tarvittavat sopimukset, luvat sekä riittävät teknilliset taidot. Paikalliset lait tulee tarkistaa. (Tero Karvinen 2023.)

### Karvinen 2006: Raportin kirjoittaminen:

-Raportin tulee olla toistettava, täsmällinen ja helppolukuinen (Tero Karvinen 2006).

-On tärkeää viitata lähteiseen. Sillä osoitettaan perehtyneisyys. Tekstin kopioiminen ja käyttäminen ilman lähdemerkintää tulkitaan sepittämiseksi tai plagioinniksi ja ne ovat rangaistavia vilppejä. (Tero Karvinen 2006.)

## Ympäristö tehtävien ratkaisussa: Acer Aspire A515-52, Windows 10, Oracle VirtualBox jolle asennettu Debian 12 Bookworm. Testisovellukset pyörii lokaalisti, selain Mozilla Firefox ja kone irti verkosta.

## a) 
Aloitin tehtävän ratkaisun kokeilemalla oppitunnilla tehtyjen johdantotehtävien ratkaisua. Ensimmäinen johdantotehtävistä ratkaistiin laittamalla urlin perään '+OR+1=1--, mutta tämä aiheutti vain "Not Found" erroria. Input-kenttä otti vastaan vain numeroita, mutta tämä on erittäin helppo kiertää tässä tapauksessa käyttämällä selaimen developer toolseja, jota kautta input-kenttä voidaan valita ja sen tyyppi vaihtaa "number" --> "", eli tyhjäksi. Tällöin input-kenttään pystyy vastaanottamaan myös kirjaimia. Käytin johdantotehtävien tekemisen tukena PortSwiggerin SQL Injection opasta ja niin tein myös tämän tehtävän kanssa.

Testisovelluksen alalaidassa oli itselleni erittäin hyödyllinen vinkki: SELECT password FROM pins WHERE pin='123'; Tämä auttoi ymmärtämään logiikkaa, millä tavoin salasanat haetaan.

PortSwiggerin "Retrieving data from other database tables" oli tässä kohtaa hyödyllinen, sillä sielä avattiin UNION keywordia ja kuinka sen avulla SELECT lauseita voidaan suorittaa. 

![Näyttökuva 2024-11-04 002630](https://github.com/user-attachments/assets/64bbb9d6-add3-4c3e-ac2f-dc259f70f0d6)

(PortSwigger 2024)

Näistä lauseista pystyi  rakentamaan logiikan omaan lauseeseen, jonka avulla adminin salasana paljastuu:

' UNION SELECT PASSWORD FROM PINS--

Admin salasana: SUPERADMIN%%rootALL-FLAG{Tero-e45f8764675e4463db969473b6d0fcdd}

## b)
Aloitin haavoittavuuden korjaamisen paikantamalla SQL-lauseen, mikä koskee salasanoja. Haavoittavuus löytyi nopeasti, eikä sen paikantaminen tuottanut ongelmia.

Tässä koodinpätkässä on SQL-injektio-haavoittuvuus, koska käyttäjän syöttämä arvo liitetään suoraan SQL-lauseeseen

![koodi_vika](https://github.com/user-attachments/assets/eda50047-a940-46b2-9b1e-5881c65ced78)

![sql_injection3](https://github.com/user-attachments/assets/75d94e95-dd93-45c7-bead-2065aa70fc7d)

(PortSwigger 2024)

PortSwiggerin How to preven SQL injection-osiossa oli juuri samantapainen haavoitttuvuus, mikä helpotti sekä paikantamista, että korjausta. Haavoittuvuuden voi ratkaista käyttämällä parametroituja SQL-kyselyitä. Korjauksessani :pin toimii paikkamerkkinä ja {"pin": pin} määrittelee sen arvon, ilman että sitä liitetään suoraan SQL-lauseeseen. Korjauksen jälkeen käyttämäni UNION SELECT-lause ei enään toimi.

![koodi_korjattu](https://github.com/user-attachments/assets/2920f52b-a98c-46d8-bd2a-06e04023676d)

![kuva](https://github.com/user-attachments/assets/c6632e01-7d3e-4e43-b1ca-8c16cda4d0d8)


## c)
Tämän tehtävän suorituksessa auttoi merkittävästi ohjattu harjoitus joka tehtiin dirfuzt-0 kohteella. Noudatin ohjeistusta kohta kohdalta ja sain asennettua tarvittavat työkalut. 

Latasin ja asensin aluksi dirfuzt-1 sovelluksen ohjeiden mukaisesti ja laitoin sen pyörimään. Irroitin läppärini verkosta.

Käytin aluksi komentoa: $ ./ffuf -w common.txt -u h<span>t</span>tp://127.0.0.2:8000/FUZZ

Sitten lähdin filtteröimään edellisen tehtävän mukaan ja käytin komentoa jolla filtteröin 154 tavun kokoiset vastaukset pois. Käytin tähän komentoa: ./ffuf -w common.txt -u h<span>t</span>tp://127.0.0.2:8000/FUZZ -fs 154

Tällä komennolla löytyi sekä admin että versionhallintaan liittyvät sivut:

![kuva (2)](https://github.com/user-attachments/assets/64a76613-3ed2-42c5-aef0-c8e86bd3755b)
![kuva (3)](https://github.com/user-attachments/assets/f0590290-9203-4250-b2dc-c9c45f994411)
![kuva (1)](https://github.com/user-attachments/assets/714cc311-fb8f-4806-9126-d969cd2924f5)
![kuva (4)](https://github.com/user-attachments/assets/7d8408f6-aeb4-4978-84ae-0f5c387b0f0a)


## d)
Tehtävän aluksi laitoin testisovelluksen päälle ohjeiden mukaisesti. Internetistä olin muiden tehtävien tapaan irtaantunut. C-tehtävän tehtävänannossa mainittiin, että kyseinen tehtävä auttaa 020-your-eyes-only-tehtävän ratkaisemisessa, joten lähdin liikkeelle käyttäen ffuff-työkalua. Suoritin aluksi komennon ($ ./ffuf -w common.txt -u h<span>t</span>tp://127.0.0.1:8000/FUZZ) ilman filtteröintiä ja se tuotti heti tulosta:

![kuva (5)](https://github.com/user-attachments/assets/20c5618b-f70c-4e35-89d0-d199070449f7)

Tämä kyseinen sanapari pomppasi silmille, josta olin kieltämättä yllättynyt. Ajattelin, että tämän löytäminen vaatisi filtteröintiä.

Nooh.. suoraan tottakai testaamaan admin-consolen lisäämistä Urlin perään, mutta ei tulosta. Hieman enemmän sovellukseen tutustuttiani päätin tehdä tunnukset sovellukseen. Sisään kirjautuneena uudelleen admin-consolen lisääminen urlin perään ja bingo!

![kuva (6)](https://github.com/user-attachments/assets/a0176695-fdc4-438f-8cbd-0be22e5db32e)

Tehtävä ratkesi lopulta helposti. Tehtävä C antoi hyvät pohjat tehtävän D ratkaisemiseksi.


## e)
Haavoittuvuuden paikantaminen lähdekoodista vei itselleni hieman aikaa. Lopulta lähdekoodia pengottuani löysin hats/views.py tiedosta koodia joka liittyy Admin consoleen. Kyseisestä tiedostosta löytyy puuttellista käyttöoikeuksien tarkistusta. AdminShowAllView-luokan test_func-metodi tarkistaa vain, että käyttäjä on kirjautunut sisään, mutta ei sitä, että onko käyttäjällä tarvittavia oikeuksia. Ylemmässä test-func-metodissa tarkistus on toteutettu self.request.user.is_staff tavalla ja lisäsinkin kyseisen koodinpätkän myös alempaan metodiin ja tämä kyseinen haavoittuvuus on tällä korjattu.

![koodi_vika2](https://github.com/user-attachments/assets/6f40cab7-8407-4ddf-a517-503c385ec553)

![koodi_korjattu2](https://github.com/user-attachments/assets/adae7d6d-d81e-4a73-adcc-116c5802a83f)

![kuva (7)](https://github.com/user-attachments/assets/03adff44-bfff-4123-9a97-5df8e0af7ae9)


## g) 
Tehtävän ratkaisuun sai osviittaa Portswiggerin SQL Injection tietopankista. "SQL injektiot" voivat teoriassa olla läsnä jokaikisellä sivustolla tai sovelluksella jos sitä vastaan ei olla suojauduttu. Tässä tehtävässä SQL injectionin pystyi toteuttamaan URL-kentän kautta. Myös esimerkiksi erilaiset input-kentät voivat toimia keinona toteuttaa "injektio". Tämä tehtävän ratkaisin jo oppitunnilla, julkaisemattomat tuotteet saa näkyviin laittamalla URL-osoitteen perään: filter?category=Gifts'+OR+1=1--. Tämä palauttaa tuotteet jossa kategoria on joko "Gifts" tai 1=1, mikä on taas aina totta, joten kaikki tuotteet tulevat näkyviin.

![sql_injection1](https://github.com/user-attachments/assets/458aa83b-d8be-46fc-8c0d-46be75e1f1d4)

## h) 
Tämänkin tehtävän ratkaisuun sai osviittaa PortSwiggerin SQL Injection tietopankista. Tällä kertaa SQL-Injektio toteutetaan input-kenttien kautta. Usernameksi laitetaan administrator'-- ja salasanaksi "". SQL-kommentti -- poistaa salasanan tarkastuksen kokonaan, jonka avulla kirjautuminen administraattorina onnistuu.

![sql_injection2](https://github.com/user-attachments/assets/9173ceff-b890-499b-bb2f-89913192fbc3)

## Lähteet
OWASP 2021. OWASP Top 10: A01 Broken Access Control. Luettavissa: https://owasp.org/Top10/A01_2021-Broken_Access_Control/. Luettu: 3.11.2024.

Tero Karvinen 2023. Find Hidden Web Directories - Fuzz URLs with ffuf. Luettavissa: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/. Luettu: 3.11.2024.

PortSwigger 2024. Access control vulnerabilities and privilege escalation. Luettavissa: https://portswigger.net/web-security/access-control. Luettu: 3.11.2024.

Tero Karvinen 2006. Raportin kirjoittaminen. Luettavissa: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/. Luettu: 3.11.2024.

PortSwigger 2024. SQL injection: What is SQL injection (SQLi)?. Luettavissa: https://portswigger.net/web-security/sql-injection#what-is-sql-injection-sqli. Luettu 3.11.2024.

PortSwigger 2024. SQL injection: how-to-prevent-sql-injection. Luettavissa: https://portswigger.net/web-security/sql-injection#how-to-prevent-sql-injection. Luettu 4.11.2024.


