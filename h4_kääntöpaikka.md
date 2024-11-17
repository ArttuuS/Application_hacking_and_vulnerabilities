## h4 Kääntöpaikka

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

![Näyttökuva 2024-11-17 124544](https://github.com/user-attachments/assets/09af1a94-8604-40c3-a10a-6257d8f3cf06)

![Näyttökuva 2024-11-17 124631](https://github.com/user-attachments/assets/31527634-6ae7-4559-8bf1-b4ff889d82ba)

![Näyttökuva 2024-11-17 124735](https://github.com/user-attachments/assets/6b87ea0e-3d2c-4587-8315-846d8d6ad4ae)

# c)



# d)

# e)

# e)

# f)

# Lähteet

https://www.reddit.com/r/bash/comments/cl54to/not_sure_why_mac_is_saying_bash_event_not_found/?rdt=58517

https://jorianwoltjer.com/blog/p/hacking/introduction-to-reverse-engineering-with-ghidra

https://medium.com/@jeanmichel.amblat/first-steps-with-ghidra-crackme01-319827a2e80b
