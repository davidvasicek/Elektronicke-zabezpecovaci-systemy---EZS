Arduino [čti Arduíno] je v informatice název malého jednodeskového počítače založeného na mikrokontrolerech ATmega od firmy Atmel. Svým návrhem se snaží podpořit výuku informatiky ve školách a seznámit studenty s tím, jak jsou pomocí počítačů řízena různá zařízení (např. mikrovlnná trouba, automatická pračka a jiné stroje). Nejedná se tedy o počítač ve smyslu stolního počítače nebo chytrého telefonu. Nelze proto k němu snadno přímo připojit monitor ani klávesnici či myš, ale je připraven na připojení LED diod, displeje z tekutých krystalů, servomotorů, senzorů, osvětlení atd. [1]


### Instalace softwaru

Open-source software Arduino IDE umožňuje snadné psaní kódu a jeho nahrávání na desku. Spouští se na systémech Windows, Mac OS X a Linux a jeho prostředí je napsáno v jazyce Java a je také založeno na zpracování a jiném open-source softwaru.
Tento software lze použít s libovolnou deskou Arduino.

1. **Stažení softwaru Arduino IDE** Software Arduino IDE je dostupný na oficiálních stráchkách společnosti Arduino [Download zde](https://www.arduino.cc/en/main/software). Instalační soubor je možné stáhnout v sekci  *Download the Arduino IDE* kliknutím na *Windows Installer* a následným kliknutím na tlačítko *JUST DOWNLOAD*

2. **Instalace softwaru Arduino IDE** Stažený instalační soubor Arduina IDE otevřeme, software nainstalujeme a následně spustíme

3. **Instalace WiFi čipu ESP 8266** Samotný software Arduino IDE neobsahuje podporu desek s WiFi čipy ESP8266, proto je nutné tuto podporu doinstalovat. Využijeme návodu vytvořeného společností Arduino-shop [Návod zde](http://navody.arduino-shop.cz/navody-k-produktum/esp8266-vyvojova-deska-wemos-d1.html). *Pozn.: Vývojovou desku nevolte dle návodu WeMos D1 (retired), ale zvolte WeMos D1 R2 & mini*.

4. **Připojení desky WeMos D1 mini** Desku WeMos D1 mini připojte kabelem Micro USB k PC, v sotwaru Arduino IDE Nástroje -> Port a zvolte port, ke kterému jste vaší desku připojili.


### Zdroje
- [1] https://cs.wikipedia.org/wiki/Arduino
