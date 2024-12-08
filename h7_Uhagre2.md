# H7 Uhagre2

## x) 

### **€ Schneier 2015: Applied Cryptography, 20ed: Chapter 1: Foundations:**

#### 1.1 Terminology:

Tässä osiossa avataan salakirjoituksen terminologiaa. Tässä termit tiivistettynä:

- **Sender and receiver (Lähettäjä ja vastaanottaja):**
  Lähettäjän tavoitteena on saada viesti vastaanottajalle turvallisesti, siten, että salakuuntelija ei pääse      viestiin käsiksi.

- **Messages and Encryption (Viestit ja salaus):**
  Viestistä sellaisenaan käytetään termejä plaintext (selkoteksti) ja cleartext (selkeäteksti. Salaus             (encryption) on taas naamiointikeino, jolla sisältö piilotetaan. Salatusta viestistä käytetään termiä           ciphertext (salateksti) ja prosessi jossa salattu viesti käännetään selkeäksi tekstiksi on decryption           (salauksen purku).

- **Authentication, Integrity, and Nonrepudiation (Todentaminen, eheys ja kiistämättömyys) :**

    -Authentication (todentaminen) = prosessi, jossa varmistetaan viestin alkuperä (oikea henkilö tai taho)
      
    -Integrity (eheys) = viittaa siihen, ettei viestiä ole muokattu siirron aikana.
      
    -Nonrepudiation (kiistämättömyys) = tarkoittaa sitä, että viestin lähettäjä ei pysty myöhemmin     
    virheellisesti kieltämään lähettäneensä viestiä.
    
- **Algorithms and Keys (algoritmit ja avaimet):**
    Cryptographic algorithm (kryptografinen algoritmi) eli salakirjoitus, on matemaattinen funktio, jota     
    käytetään viestin salaamiseen ja salauksen purkamiseen. Modernissa kryptografialla käytetään avaimia sekä 
    salaukseen että sen purkuun.

- **Symmetric Algorithms (symmetriset algoritmit):**
    Symmetrisissä algoritmeissa salaus- ja purkuavain ovat useimmiten samat ja niiden turvallisuus perustuu         avaimen salaisuuteen.

- **Public-Key Algorithms (julkisen avaimen algoritmit):**
    Julkisen avaimen algoritmit ovat vastakohta symmetrisille. Siinä salaus- ja purkuavaimet ovat erilaiset.        Kuka tahansa voi käyttää avainta viestin salaamiseen, mutta vain ne joilla on vastaava purkuavain, voi          purkaa viestin.

- **Cryptanalysis (kryptoanalyysi):**
    Kryptoanalyysi on tiivistettynä tiede, joka pyrkii palauttamaan viestin selkokielisen sisällön ilman pääsyä     avaimen tietoon. Onnistunut kryptonalyysi voi paljastaa joko selkokielisen viestin tai avaimen.

- **Security of Algorithms (algoritmien turvallisuus):**
    Algoritmit tarjoavat eri tason turvallisuutta ja niiden murtamisen vaikeus määrittää niiden turvallisuuden      tason.

#### 1.4 Simple XOR:
   -XOR on looginen operaattori joka vertailee kahta bittiä ja palauttaa arvon 1, jos bitit ovat erilaisia tai 
    0, jos ne ovat samoja. XOR ei tarjoa oikeaa turvallisuutta lainkaan ja se on helppo murtaa, jopa ilman 
    tietokonetta.

#### 1.7 Large Numbers:
   -Tässä osiossa avataan isoja lukuja.

**Karvinen 2024: Python Basics for Hackers:**
    -Tässä artikkelissa avataan Pythonin perusteita hakkeroinnissa.

## a)

## b)

## c)

## d)

## Lähteet


