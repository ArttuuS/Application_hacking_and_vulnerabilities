# h2 Break & unbreak

## x)
### OWASP: OWASP Top 10: A01 Broken Access Control & PortSwigger: Access control vulnerabilities and privilege escalation:

-Yksi yleinen tietoturvaongelma on "Broken Access Control" (suom. rikkinäiset käyttöoikeudet), jossa käyttäjä voi päästä käsiksi tietoihin tai toimintoihin, joihin hänellä ei pitäisi olla pääsyä. Tämä voi johtaa luvattomaan tiedon katseluun, muokkaamiseen, poistamiseen tai liiketoimintaprosessien väärinkäyttöön. (OWASP 2021.)

-Yleisiä "Broken Access Control" haavoittuvuuksia on mm. liian laajat käyttöoikeudet, URL-osoitteiden muokkaaminen ja API:n käyttäminen ilman pääsynhallintaa POST-, PUT- ja DELETE-toiminnoille (OWASP 2021).

-"Access control" (pääsynhallinta) on hyödyllistä vain palvelinpuolen koodissa tai palvelimettomassa API:ssa, jossa mahdollinen hyökkääjä ei pysty muokkaamaan pääsynhallintaa (OWASP 2021).

-Turvatoimia, joilla hyökkäyksiä voidaan estää on mm. oletusarvoinen käyttöoikeuksien esto (ei julkisille resursseille), pääsynhallinta mekanismien käyttö yhtenäisesti koko sovellukselle ja pääsynhallinnan epäonnistumisten kirjaaminen ylös. Näitä turvatoimia tulee testata. (OWASP 2021.)

-"Vertical access controls": käyttöoikeusien hallintaa, jolla rajoitetaan herkkiin toimintoihin pääsyä eri käyttäjäryhmille (esim. admin voi muokata ja poistaa minkä tahansa tilin, mutta tavallinen käyttäjä ei). "Horizontal access controls": käyttöoikeuksien hallinan mekanismeja jotka rajoittavat oikeuksia tietyille käyttäjille (esim. käyttäjä x voi tarkastella oman pankkitilinsä tapahtumia mutta ei käyttäjän y tapahtumia). "Context-dependent access controls": käyttöoikeuksien hallintaa, jonka avulla rajoitetaan toimintoihin pääsyä sovelluksen tilan tai käyttäjän toimenpiteiden perusteella (esim. käyttäjä ei voi muokata ostoskorin sisältöä, maksamisen jälkeen). (PortSwigger 2024.)

### Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf:

-Verkkopalvelimilla on usein salaisia hakemistoja. Näitä voidaan etsiä automaattisesti käyttäen Fuff-työkalua. (Tero Karvinen 2023.)

-Suodattamalla vastauksia, voidaan saavuttaa tarkemmat tulokset (Tero Karvinen 2023).

-Ennen penetraatio työkalujen ja menetelmien käyttöä (sis. fuff), tulee varmistaa tarvittavat sopimukset, luvat sekä riittävät teknilliset taidot. Paikalliset lait tulee tarkistaa. (Tero Karvinen 2023.)

### Karvinen 2006: Raportin kirjoittaminen:

-Raportin tulee olla toistettava, täsmällinen ja helppolukuinen (Tero Karvinen 2006).

-On tärkeää viitata lähteiseen. Sillä osoitettaan perehtyneisyys. Tekstin kopioiminen ja käyttäminen ilman lähdemerkintää tulkitaan sepittämiseksi tai plagioinniksi ja ne ovat rangaistavia vilppejä. (Tero Karvinen 2006.)

### Vapaaehtoinen PortSwigger 2020: What is SQL injection? - Web Security Academy:








## a)

## b)

## c)

## d)

## e)

## g)

## h)

## Lähdeviitteet

OWASP 2021. OWASP Top 10: A01 Broken Access Control. Luettavissa: https://owasp.org/Top10/A01_2021-Broken_Access_Control/. Luettu: 3.11.2024.

Tero Karvinen 2023. Find Hidden Web Directories - Fuzz URLs with ffuf. Luettavissa: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/. Luettu: 3.11.2024.

PortSwigger 2024. Access control vulnerabilities and privilege escalation. Luettavissa: https://portswigger.net/web-security/access-control. Luettu: 3.11.2024.

Tero Karvinen 2006. Raportin kirjoittaminen. Luettavissa: https://terokarvinen.com/2006/raportin-kirjoittaminen-4/. Luettu: 3.11.2024.





