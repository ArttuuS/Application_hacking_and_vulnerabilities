## h6 Sulaa hulluutta

## a)

Aloitin tehätävän lataamalla tiedoston koneelleni. Suoritin Linuxin "File-komennon" joka palauttaa yleistä tietoa tiedostosta. Syötteestä voi päätellä muun muassa, että tiedosto on JPEG-kuvatiedosto, tiedosto sisältää 6 tietuetta ja resoluution on 1024 x 1024.

![Näyttökuva 2024-12-01 221039](https://github.com/user-attachments/assets/1264fb0f-f345-447f-83fa-42670dd8eac0)

Jatkoin tutkintaa strings-komennolla. Pelkkä strings h1.jpg - komento antoi ison määrän epämääräisiä kirjan-numero-yhdistelmiä joten muokkasin komennon muotoon : strings -n 15 h1.jpg joka palauttaa vain vähintään 15 merkkiä pitkät stringit. Tällä saatiin filtteröityä hakutulosta parempaan muotoon ja selvisi, että tiedostossa on useita xml-tiedostoja.

![Näyttökuva 2024-12-01 220904](https://github.com/user-attachments/assets/e777dec3-7ae3-4744-8e3b-7b25f679fb7b)

## b)

Jatkoin tiedoston tutkimista binwalkilla. Asensin ohjelman ja suoritin ensimmäisen "binwalk h1.jpg" - komennon, jolla selvisi että xml-tiedostot on pakattuja ZIP-tiedostoja. 

![Näyttökuva 2024-12-01 221349](https://github.com/user-attachments/assets/8821edfd-139e-41fc-bb1e-2abe987b9c88)

Suoritin myös komennon "binwalk -a" joka skannaa tiedoston etsien suoritettavia opcode-allekirjoituksia. Näitä ei kuitenkaan löytynyt.

![Näyttökuva 2024-12-01 221608](https://github.com/user-attachments/assets/d0cb128e-3f18-450f-9751-92daaa1db610)

Seuraavaksi suoritin komennon "binwalk -e h1.jpg" joka purkaa tunnetut tiedostotyypit automaattisesti. Komento loi erillisen kansion "_h1-jpg.extracted" johon tiedostot on eritelty. 

![Näyttökuva 2024-12-01 221753](https://github.com/user-attachments/assets/2d4d5d6e-1301-45f2-867a-e9437033de85)

![Näyttökuva 2024-12-01 221842](https://github.com/user-attachments/assets/7f42091f-6067-41d3-9fb4-8858e7d2d570)



## c)
