Arduino [čti Arduíno] je v informatice název malého jednodeskového počítače založeného na mikrokontrolerech ATmega od firmy Atmel. Svým návrhem se snaží podpořit výuku informatiky ve školách a seznámit studenty s tím, jak jsou pomocí počítačů řízena různá zařízení (např. mikrovlnná trouba, automatická pračka a jiné stroje). Nejedná se tedy o počítač ve smyslu stolního počítače nebo chytrého telefonu. Nelze proto k němu snadno přímo připojit monitor ani klávesnici či myš, ale je připraven na připojení LED diod, displeje z tekutých krystalů, servomotorů, senzorů, osvětlení atd. [1]


### Instalace softwaru

Open-source software Arduino IDE umožňuje snadné psaní kódu a jeho nahrávání na desku. Spouští se na systémech Windows, Mac OS X a Linux a jeho prostředí je napsáno v jazyce Java a je také založeno na zpracování a jiném open-source softwaru.
Tento software lze použít s libovolnou deskou Arduino.

1. **Stažení softwaru Arduino IDE** Software Arduino IDE je dostupný na oficiálních stráchkách společnosti Arduino [Download zde](https://www.arduino.cc/en/main/software). Instalační soubor je možné stáhnout v sekci  *Download the Arduino IDE* kliknutím na *Windows Installer* a následným kliknutím na tlačítko *JUST DOWNLOAD*

2. **Instalace softwaru Arduino IDE** Stažený instalační soubor Arduina IDE otevřeme, software nainstalujeme a následně spustíme

3. **Instalace WiFi čipu ESP 8266** Samotný software Arduino IDE neobsahuje podporu desek s WiFi čipy ESP8266, proto je nutné tuto podporu doinstalovat. Využijeme návodu vytvořeného společností Arduino-shop [Návod zde](http://navody.arduino-shop.cz/navody-k-produktum/esp8266-vyvojova-deska-wemos-d1.html). *Pozn.: Vývojovou desku nevolte dle návodu WeMos D1 (retired), ale zvolte WeMos D1 R2 & mini*.

4. **Připojení desky WeMos D1 mini** Desku WeMos D1 mini připojte kabelem Micro USB k PC, v sotwaru Arduino IDE Nástroje -> Port a zvolte port, ke kterému jste vaší desku připojili.

### Haedware

- **WeMos D1 Mini** - Wemos D1 Mini je Wifi vývojová breadbord kompatibilní deska, založená na ESP8266 [e-shop](https://arduino-shop.cz/arduino/1679-externi-konektor-anteny-wemos-d1-mini-pro-16mb-1501219041.html?gclid=EAIaIQobChMInLuQ9d_A2QIVhOcbCh35RwMeEAQYASABEgJ-zvD_BwE)
- **Senzor Plamene Infračervený Detekční Modul** - Modul detekuje plamen nebo podobné světlo o vlnové délce 760nm. [e-shop](https://arduino-shop.cz/arduino/1520-senzor-plamene-infracerveny-detekcni-modul-1486113741.html) | [návod](http://navody.arduino-shop.cz/navody-k-produktum/infracerveny-senzor-plamene.html)
- **BME280 Modul Měření Teploty Vlhkosti** - Modul pro měření teploty, vlhkosti a barometrického tlaku obsahuje precizní senzor BME280. Tento měřící senzor od firmy Bosch komunikuje přes rozhraní I2C a zvládá komunikovat rychlostí až 3,4 MHz. [e-shop](https://arduino-shop.cz/arduino/1361-bme280-modul-mereni-teploty-vlhkosti-a-barometrickeho-tlaku-precizni-1469214547.html) | [návod](http://navody.arduino-shop.cz/navody-k-produktum/senzor-bme280-mereni-teploty-relativni-vlhkosti-a-barometrickeho-tlaku.html) | [datasheet](https://arduino-shop.cz/docs/produkty/0/91/1469214547.pdf) | [knihovna](http://navody.arduino-shop.cz/docs/texty/0/123/bme280_knihovna.zip)
- **Vodiče, jumpers** - [e-shop F-F + F-M + M-M](https://arduino-shop.cz/arduino/1314-sada-dupont-vodicu-120-kusu-mm-ff-mf-3-druhy-1464646471.html) | [e-shop F-F](https://arduino-shop.cz/arduino-kabelaz-propoje-rozsireni/835-arduino-vodice-samice-samice-40-kusu-1500635965.html) | [e-shop F-M](https://arduino-shop.cz/arduino-kabelaz-propoje-rozsireni/1214-arduino-vodice-samice-samice-40-kusu-1457705007.html) | [e-shop M-M](https://arduino-shop.cz/arduino-kabelaz-propoje-rozsireni/1063-arduino-vodice-samec-samec-40-kusu-1500635966.html) 
- **Kontaktní nepájivé pole** - [e-shop](https://www.gme.cz/nepajive-kontaktni-pole-zy-204) 
- **LED (3x)** - [e-shop](https://www.gme.cz/led-5mm-warm-white-8500-30)
- **Rezistor 220 ohm (3x)** - [e-shop](https://www.gme.cz/rm-220r-0309-1w-1)
- **Mikrospínač (3x)** - [e-shop](https://www.gme.cz/tc-0102-t-a00) 

### Zapojení

![zapojeni](https://github.com/davidvasicek/Elektronicke-zabezpecovaci-systemy---EZS/blob/master/img/Zapojeni1.png)





- **Raspberry Pi** - Výhodná sada Raspberry Pi 3, 16GB karta, chladič, 2.5A zdroj, Onenine, černá [e-shop](http://rpishop.cz/raspberry-pi-sady/299-raspberry-pi-3-vyhodna-sada-krabicka-onenine.html)


### Zdroje
- [1] https://cs.wikipedia.org/wiki/Arduino
