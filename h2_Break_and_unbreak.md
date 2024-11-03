# h2 Break & unbreak

## x)
### OWASP: OWASP Top 10: A01 Broken Access Control & PortSwigger: Access control vulnerabilities and privilege escalation:

-Yksi yleinen tietoturvaongelma on "Broken Access Control" (suom. rikkinäiset käyttöoikeudet), jossa käyttäjä voi päästä käsiksi tietoihin tai toimintoihin, joihin hänellä ei pitäisi olla pääsyä. Tämä voi johtaa luvattomaan tiedon katseluun, muokkaamiseen, poistamiseen tai liiketoimintaprosessien väärinkäyttöön. (viite)

-Yleisiä "Broken Access Control" haavoittuvuuksia on mm. liian laajat käyttöoikeudet, URL-osoitteiden muokkaaminen ja API:n käyttäminen ilman pääsynhallintaa POST-, PUT- ja DELETE-toiminnoille. (viite)

-"Access control" (pääsynhallinta) on hyödyllistä vain palvelinpuolen koodissa tai palvelimettomassa API:ssa, jossa mahdollinen hyökkääjä ei pysty muokkaamaan pääsynhallintaa. (viite)

-Turvatoimia, joilla hyökkäyksiä voidaan estää on mm. oletusarvoinen käyttöoikeuksien esto (ei julkisille resursseille), pääsynhallinta mekanismien käyttö yhtenäisesti koko sovellukselle ja pääsynhallinnan epäonnistumisten kirjaaminen ylös. Näitä turvatoimia tulee testata! (viite)

-"Vertical access controls": käyttöoikeusien hallintaa, jolla rajoitetaan herkkiin toimintoihin pääsyä eri käyttäjäryhmille (esim. admin voi muokata ja poistaa minkä tahansa tilin, mutta tavallinen käyttäjä ei). "Horizontal access controls": käyttöoikeuksien hallinan mekanismeja jotka rajoittavat oikeuksia tietyille käyttäjille (esim. käyttäjä x voi tarkastella oman pankkitilinsä tapahtumia mutta ei käyttäjän y tapahtumia). "Context-dependent access controls": käyttöoikeuksien hallintaa, jonka avulla rajoitetaan toimintoihin pääsyä sovelluksen tilan tai käyttäjän toimenpiteiden perusteella (esim. käyttäjä ei voi muokata ostoskorin sisältöä, maksamisen jälkeen).

### Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf:

-Verkkopalvelimilla on usein salaisia hakemistoja. Näitä voidaan etsiä automaattisesti käyttäen Fuff-työkalua. (viite)

-Suodattamalla vastauksia, voidaan saavuttaa tarkemmat tulokset. (viite)

-Ennen penetraatio työkalujen ja menetelmien käyttöä (sis. fuff), tulee varmistaa tarvittavat sopimukset, luvat sekä riittävät teknilliset taidot. Paikalliset lait tulee tarkistaa! (viite)

### Karvinen 2006: Raportin kirjoittaminen:

-Raportin tulee olla toistettava, täsmällinen ja helppolukuinen.

-On tärkeää viitata lähteiseen. Sillä osoitettaan perehtyneisyys. Tekstin kopioiminen ja käyttämäminen ilman lähdemerkintää tulkitaan sepittämiseksi tai plagioinniksi ja ne ovat rangaistavia vilppejä. (viite)

### Vapaaehtoinen PortSwigger 2020: What is SQL injection? - Web Security Academy:








## a)

## b)

## c)

## d)

## e)

## g)

## h)

## Lähdeviitteet
