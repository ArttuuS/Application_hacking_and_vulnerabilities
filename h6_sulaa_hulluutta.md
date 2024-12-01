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

Tutkin eri xml-tiedostoja, joista silmiin pomppasi erityisesti tiedosto "document.xml". Tämä tiedosto sisälsi erinäisiä "sitaatteja" tulevaisuudesta:

![Näyttökuva 2024-12-01 222403](https://github.com/user-attachments/assets/c0c541c9-77b8-4e2e-852d-56e44455eec7)

Purin myös  kansion "494F5.zip" joka sisälsi samankaltaisen rakenteen kuin itse päähakemisto. Sieltä löytyi myös sama document.xml tiedosto joka sisälsi samoja sitaatteja:

![Näyttökuva 2024-12-01 222835](https://github.com/user-attachments/assets/dd52b44d-4334-4d60-a673-7ecd9aa45f9d)

![Näyttökuva 2024-12-01 222816](https://github.com/user-attachments/assets/e41ae3cd-3939-4ea9-8b22-8a62f943cd3f)

"Raw Data - analyysia" varten on komento binwalk --dd='.*' , jonka avulla raw datan voi dumpata manuaalisesti. Tämä kannatti, sillä se paljasti tiedostosta lisää kuvia:

![Näyttökuva 2024-12-01 225408](https://github.com/user-attachments/assets/1b9aa24f-b1a6-405c-a20b-6f07966aa1f0)

![Näyttökuva 2024-12-01 225431](https://github.com/user-attachments/assets/b368252e-6907-453c-b89c-a4f50fc2458c)

## c)

Valitsin listasta sovelluksen [Fermata](https://github.com/AndreyPavlenko/Fermata), joka on ilmainen video- ja tv-soitin. Latasin sovelluksen APK:n ja asensin sekä JADX- että Bytecode-viewer-työkalut. 

Molempien työkalujen toimintaperiaate on hyvin samankaltainen. Työkaluihin vain raahataan haluttu tiedosta jonka jälkeen tiedosto on helposti tutkittavissa. 

![Näyttökuva 2024-12-02 000155](https://github.com/user-attachments/assets/65e5dfa9-fef5-4c70-b341-ba5c96f46f87)

![Näyttökuva 2024-12-02 000658](https://github.com/user-attachments/assets/30d1c455-1caa-42f5-b22a-396adba64483)

![Näyttökuva 2024-12-02 001151](https://github.com/user-attachments/assets/d41249c0-de06-4883-b65b-9d2e4ec2e651)


