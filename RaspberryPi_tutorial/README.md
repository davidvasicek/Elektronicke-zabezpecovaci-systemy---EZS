![alt text](https://github.com/davidvasicek/Elektronicke-zabezpecovaci-systemy---EZS/blob/master/img/raspberry-pi-logo%20-%20kopie.png)

**Raspberry Pi** (výslovnost [ˈraːzbəri pai]) je v informatice název malého jednodeskového počítače s deskou plošných spojů o velikosti zhruba platební karty. V roce 2012 byl vyvinut britskou nadací Raspberry Pi Foundantion s cílem podpořit výuku informatiky ve školách a seznámit studenty s tím, jak mohou počítače řídit různá zařízení (např. mikrovlnná trouba, automatická pračka). Primárním operačním systémem je Raspbian. Cena je na konci roku 2016 v rozmezí 150–1 200 Kč (nejlevnější je Raspberry Pi Zero, nejdražší pak Raspberry Pi 3 Model B). Označení „Raspberry Pi“ je registrovanou ochrannou známkou, a proto mají podobně navržené počítače zdánlivě odvozené názvy (např. Banana Pi) [1]

### Instalace OS

**Raspbian** ( anglická výslovnost [raːzbiən] IPA ) je operační systém odvozený od Debianu pro Raspberry Pi i osobní počítače . [2] Je oficiálně poskytován nadací Raspberry Pi Foundation jako primární operační systém pro jednoplášťové počítače z rodiny Raspberry Pi. [1] Raspbian byl vytvořen Mikem Thompsonem a Peterem Greenem jako nezávislý projekt. [5] První sestavení byla dokončena v červnu 2012. [6] Raspbian je vysoce optimalizovaný pro ARM procesory používané v Raspberry Pi. [2]

1. **Stažení operačního systému.** Raspbian je součásti instalačního balíčku zvaného NOOBS, který nalezneme na oficiálních stránkách organizace RaspberryPi [Download zde](https://www.raspberrypi.org/downloads/noobs/). Stáhneme NOOBS ve formátu .zip kliknutím na tlačítko *Download ZIP*.
2. **Příprava Micro SD karty.** Pokud naše karta obsahuje zastaralá data, bude nutné kartu v prvé řadě naformátovat. To provedeme programem zvaným SD Memory Card Formatter [Download zde](https://www.sdcard.org/downloads/formatter_4/).
3. **Kopírování souborů na Micro SD kartu.** Jestliže máme balíček NOOBS stažený a paměťovou kartu naformátovanou, překopírujeme veškeré soubory ze ZIP archívu balíčku NOOBS na paměťovou kartu.
4. **Instalace OS.** Paměťovou kartu vložíme do našeho zařízení Raspberry Pi a připojíme monitor a napájení. Po nabootování paměťové karty se zobrazí nabídka, ve které zaškrtávacím políčkem zvolíme *Raspbian with PIXEL* a stiskem tlačítka *Install* system Raspbian nainstalujeme.

### Prvotní nastavení systému

1. **Připojení k internetu.** 

    - **Kabelové připojení (ETH0):** V případě kabelového ethernetového připojení pouze připojíme datový kabel do zařízení Raspberry Pi. 
    - **Bezdrátové připojení (WLAN0):** Pokud budeme využívat WiFi připojení, nalezneme v grafickém prostředí OS Raspbianu v pravé horní části obrazovky ikonku WiFi, na kterou klikneme, vybereme SSID sítě, ke které se budeme připojovat a vložíme heslo. 
    - **Získáni IP adresy:** Spusťte příkazový řádek a zadejte příkaz `ifconfig`. IP adresu najdeme pod označením *inet*. V případě kabelového připojení v *ETH0*, v případě bezdrátového připojení *WLAN0*.
2. **Povolení protokolu SSH (Secure Shell).** 

### Zdroje
- [1] https://cs.wikipedia.org/wiki/Raspberry_Pi
- [2] https://cs.wikipedia.org/wiki/Raspbian
