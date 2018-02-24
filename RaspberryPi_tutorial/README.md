![alt text](https://github.com/davidvasicek/Elektronicke-zabezpecovaci-systemy---EZS/blob/master/img/raspberry-pi-logo%20-%20kopie1.png)

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
2. **Povolení protokolu SSH (Secure Shell).** v prostředí OS Raspbianu klikneme v levém horním rohu na ikonu maliny -> Preferences -> Raspberry Pi Configuration -> Interfaces -> SSH: Enable -> OK [Návod zde](https://www.raspberrypi.org/documentation/remote-access/ssh/).
3. **Update a Upgrade systému.** Spusťte příkazový řádek a zadejte příkaz `sudo apt-get -y upgrade`, po dokončení zadejte příkaz `sudo apt-get -y update`
### Instalace repozitářů
Přejděte do příkazového řádku a přihlaste se jako uživatel správce root příkazem `sudo -i`. Pokud nebudete jako správce přihlášeni, budou vám chybět oprávnění k následujícím úkonům.

1. **Instalace FTP**. FTP (File Transfer Protocol) slouží pro přenos souborů mezi Raspberry Pi a jiným počítačem.

    ```
    apt-get install -y vsftpd
    nano /etc/vsftpd.conf 
    	// změťe #write_enable=YES na write_enable=YES
    /etc/init.d/vsftpd restart
    ```
2. **Instalace MariDB.** MariDB je relační databáze, která je komunitou vyvíjenou nástupnickou větví (tzv, „forkem“) MySQL. Hlavním důvodem k vytvoření této větve bylo udržení licence svobodného softwaru GNU GPL. [odkaz10]

    ```
	sudo apt install -y mariadb-server
    ```
	
3. **Instalace Node JS a npm.** Node.js je softwarový systém navržený pro psaní vysoce škálovatelných internetových aplikací, především webových serverů. Programy pro Node.js jsou psané v jazyce JavaScript, hojně využívající model událostí a asynchronní I/O operace pro minimalizaci režie procesoru a maximalizaci výkonu [4]. Npm je správce balíčků pro programovací jazyk JavaScript. [5]
    
    ``` 
	curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
	apt-get install nodejs
	node -v
	npm -v
    ``` 
   
   vytvoření ukázkového skriptu:
    ```
    mkdir /home/pi/nodejs
    cd /home/pi/nodejs
    nano test.js
    	console.log("Hello world");
    node test.js
	``` 
4. **Vytvoření bezdrátového přístupového bodu.** Raspberry Pi může být používán jako bezdrátový přístupový bod, který má samostatnou síť. To lze provést pomocí vestavěných bezdrátových prvků Raspberry Pi 3 nebo Raspberry Pi Zero W nebo pomocí vhodného bezdrátového USB klíče, který podporuje přístupové body. Bezdrátový přístupový bod vytvoříte dle náslodujícího tutoriálu [Tutorial zde](https://www.raspberrypi.org/documentation/configuration/wireless/access-point.md)
	
### Konfigurace projektu
V této fázi máme připravené Raspberry Pi pro samotnou konfiguraci projektu a následující části se proto budeme věnovat postupy konfigurace našeho serveru.

1. **Vytvoření nové databáze a potřebných tabulek.** V příkazovém řádku zadejte příkaz `mysql -u root -p` a zadejte heslo. Pozn.: Heslo jsme volili při instalaci databázového serveru. Při zadávání příkazů nezapomeňte na konci každého příkazu zadat znak středníku.
	``` 
	CREATE DATABASE IoT;  // Vytvoří novou databázi s názvem IoT
	USE IoT;  // Přepneme se do nově vytvořené databáze IoT
	```
	
2.  **Vytvoření nové tabulky ArduinoDevices** - Tato tabulka bude sloužit pro registraci jednotlivých zařízení Arduino, které se na serveru budou registrovat. Obsahuje celkem 4 atributy: 
	
		- **id**: identifikátor záznamů v tabulce
		- **DeviceIP**: IP adresu daného zařízení, abychom jej v síti mohli najít
		- **DeviceID**: jedinečné identifikační číslo daného zařízení (jedná se o MAC adresu zařízení)
		- **Description**: popis zařízení, aby bylo jednodušší zařízení námi identifikovat
         
		```
		CREATE TABLE IF NOT EXISTS ArduinoDevices(
		id INT(20) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
		DeviceIP VARCHAR(100) NOT NULL,
		DeviceID VARCHAR(100) NOT NULL,
		Description VARCHAR(500) NOT NULL
		);
		```
		 
3. **Vytvoření nové tabulky BME280sensors** - Tato tabulka bude slouži pro ukládání záznamů z teplotních a tlakových senzoru BME280, které budou na server odesílat výše registrované zařízení Arduino. Obsahuje celkem 6 atributů:
	
		- id: identifikátor záznamů v tabulce
		- DeviceID: Identifikační číslo zařízení, které data zaslalo
		- Temperature: data o teplotě [°C]
		- Humidity: data o vlhkosti [%]
		- Pressure: data o barometrickém tlaku [hPa]
		- TimeStamp: čas, ve který server data obdržel
	
		```
		CREATE TABLE IF NOT EXISTS BME280sensors(
		id INT(20) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
 		ArduinoID VARCHAR(100) NOT NULL,
 		Temperature FLOAT(3) NOT NULL,
 		Humidity FLOAT(3) NOT NULL,
 		Pressure FLOAT(3) NOT NULL,
 		TimeStamp NUMERIC(20) NOT NULL
		);
		```
	


CREATE TABLE IF NOT EXISTS AndroidDevices(
 id INT(20) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
 Token VARCHAR(200) NOT NULL,
 Device_Name VARCHAR(100) NOT NULL,
 Device_ID VARCHAR(100) NOT NULL
);
	
### Zdroje
- [1] https://cs.wikipedia.org/wiki/Raspberry_Pi
- [2] https://cs.wikipedia.org/wiki/Raspbian
- [3] https://cs.wikipedia.org/wiki/LAMP
- [4] https://cs.wikipedia.org/wiki/Node.js
- [5] https://en.wikipedia.org/wiki/Npm_(software)

odkaz10 - https://cs.wikipedia.org/wiki/MariaDB
