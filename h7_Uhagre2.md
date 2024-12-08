# H7 Uhagre2

## x) 

**€ Schneier 2015: Applied Cryptography, 20ed: Chapter 1: Foundations:**

1.1 Terminology:

Tässä osiossa avataan salakirjoituksen terminologiaa. Tässä termit tiivistettynä:

- Sender and receiver (Lähettäjä ja vastaanottaja):

    Lähettäjän tavoitteena on saada viesti vastaanottajalle turvallisesti, siten, että salakuuntelija ei pääse      viestiin käsiksi.

- Messages and Encryption (Viestit ja salaus):
    
    Viestistä sellaisenaan käytetään termejä plaintext (selkoteksti) ja cleartext (selkeäteksti. Salaus             (encryption) on taas naamiointikeino, jolla sisältö piilotetaan. Salatusta viestistä käytetään termiä           ciphertext (salateksti) ja prosessi jossa salattu viesti käännetään selkeäksi tekstiksi on decryption           (salauksen purku).

- Authentication, Integrity, and Nonrepudiation:

    -Authentication (todentaminen) = prosessi, jossa varmistetaan viestin alkuperä (oikea henkilö tai taho)
  
    -Integrity (eheys) = viittaa siihen, ettei viestiä ole muokattu siirron aikana.
  
    -Nonrepudiation (kiistämättömyys) = tarkoittaa sitä, että viestin lähettäjä ei pysty myöhemmin     
     virheellisesti kieltämään lähettäneensä viestiä.
    
- Algorithms and Keys:
  
     Cryptographic algorith (kryptografinen algoritmi) eli salakirjoitus, on matemaattinen funktio, jota     
     käytetään viestin salaamiseen ja salauksen purkamiseen. Modernissa kryptografialla käytetään avaimia sekä 
     salaukseen että sen purkuun.

- Symmetric Algorithms:

     Symmetrisissä algoritmeissa salaus- ja purkuavain ovat useimmiten samat ja niiden turvallisuus perustuu         avaimen salaisuuteen.

- Public-Key Algorithms:

    Julkisen avaimen algoritmit ovat vastakohta symmetrisille. Siinä salaus- ja purkuavaimet ovat erilaiset.        Kuka tahansa voi käyttää avainta viestin salaamiseen, mutta vain ne joilla on vastaava purkuavain, voi          purkaa viestin.

- Cryptanalysis:

    Kryptoanalyysi on tiivistettynä tiede, joka pyrkii palauttamaan viestin selkokielisen sisällön ilman pääsyä     avaimen tietoon. Onnistunut kryptonalyysi voi paljastaa joko selkokielisen viestin tai avaimen.

- Security of Algorithms:

    Algoritmit tarjoavat eri tason turvallisuutta ja niiden murtamisen vaikeus määrittää niiden turvallisuuden      tason.

1.4 Simple XOR:

    XOR on looginen operaattori joka vertailee kahta bittiä ja palauttaa arvon 1, jos bitit ovat erilaisia tai 
    0, jos ne ovat samoja. XOR ei tarjoa oikeaa turvallisuutta lainkaan ja se on helppo murtaa, jopa ilman 
    tietokonetta.

1.7 Large Numbers:

**Karvinen 2024: Python Basics for Hackers:**

**Vapaaehtoinen: Karvinen 2024: Get started Micro Editor:**

**Vapaaehtoinen: Karvinen 2024: Getting Started with Cryptopals using Python:**

## a)

## b)

## c)

## d)

## Lähteet


