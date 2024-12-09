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

### **Karvinen 2024: Python Basics for Hackers:**
   -Tässä artikkelissa avataan Pythonin perusteita hakkeroinnissa.

## a)

Convert hex to base64

Aloitin tämän tehtävän tekemisen googlaamalla "hex to base64 python" ja löysin erittäin hyödyllisen stackoverflow keskustelun (löytyy liitteistä) aiheesta. Sieltä löysin myös koodiesimerkin jolla muutos tehdään. Koodissa käytetään pythonin b64encode() funktiota.

![Näyttökuva 2024-12-09 020711](https://github.com/user-attachments/assets/3a37b19b-4c73-487b-9c28-a38a642d4717)

![Näyttökuva 2024-12-09 020742](https://github.com/user-attachments/assets/d67201ca-d68e-4078-972c-e39a9ea4522e)


## b)

Fixed XOR

Tätä tehtävää lähdin lähestymään samalla lähestymistavalla. Googlettelin aiheesta ja löysin hyvän artikkelin GeeksForGeeks-sivustolta (löytyy liitteistä). Siinä kerrottiin Pythonin bytes.fromhex() funktiosta jolla  voi tehdä muutoksen hexadesimaalista binaariksi.

XOR-operaatioon kysyin apua ChatGPT:ltä sillä olin melko hukassa, että miten toiminto tulee koodata.  Tämän jälkeen muuttaminen takaisin hexadesimaaliksi onnistuu helposti hex() funktiolla.

![Näyttökuva 2024-12-09 024640](https://github.com/user-attachments/assets/9f61737a-1bbc-46ef-bb6e-859cd44d525d)

![Näyttökuva 2024-12-09 024713](https://github.com/user-attachments/assets/1460e7f7-ac7e-49a8-82cf-723141dcb20d)


## c)

Tätäkin tehtävää lähestyin googlaamalla aiheesta. Tehtävä tuntui itselleni vaikealta enkä suoraan keksinyt itse ratkaisua millä lähtisin lähestymään ongelmaa. Löysin stackoverflow-sivustolta malliratkaisun mikä näytti toimivan. En tietenkään tästä pisteitä ansaitse, mutta yritin ymmärtää koodin toimintaa:

-Koodissa käytetään unhexlify-funktiota heksadesimaalisen merkkijonon muuttamiseen tavudataksi.

-Koodissa luodaan generaattori jolla yritetään kaikkia mahdollisia salauksen purkamisen avaimia.

-Lopuksi tulostetaan se merkkijono jossa on eniten välilyöntejä.

![Näyttökuva 2024-12-09 032239](https://github.com/user-attachments/assets/77f9afff-1350-4dc9-b8f3-d0b5ef7adfbb)

![Näyttökuva 2024-12-09 032250](https://github.com/user-attachments/assets/55f6005b-5c7c-49d7-9668-3bd63f0fe4fa)

## d)

Löysin tähän tehtävään googlaamalla useita eri ratkaisuja, mutta päätän olla kopioimatta niitä sillä en ymmärrä niiden toimintalogiikkaa. Aiheeseen pitäisi tutustua paremmin jotta voisin luoda oman koodin "from scratch".

## Lähteet

Stack Overflow 2015. Hex to Base64 conversion in Python. Luettavissa: https://stackoverflow.com/questions/33704327/hex-to-base64-conversion-in-python. Luettu 9.12.2024.

GeeksforGeeks 2024. Convert Hex String to Bytes in Python. Luettavissa: https://www.geeksforgeeks.org/convert-hex-string-to-bytes-in-python/. Luettu 9.12.2024.

€ Schneier 2015: Applied Cryptography, 20ed: Chapter 1: Foundations. Luettavissa: https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/08_chap01.html#chap01-sec001. Luettu 9.12.2024

Tero Karvinen 2024. Python Basics for Hackers. Luettavissa: https://terokarvinen.com/python-for-hackers/. Luettu 9.12.2024.

Stack Overflow 2017. Luettavissa: https://stackoverflow.com/questions/41819489/single-byte-xor-cipher-python. Luettu 9.12.2024.

[chatgpt](https://chatgpt.com/)
