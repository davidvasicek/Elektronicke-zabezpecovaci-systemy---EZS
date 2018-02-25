## Arduino

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

Schéma zapojení bylo vytvořeno v open-source software Fritzing. Tento software můžeme stáhnout ze stránek [http://fritzing.org/download/](http://fritzing.org/download/) 


### Kód



```c++
#include <ESP8266WiFi.h>
#include <WiFiUdp.h>
#include <Wire.h>
#include <SPI.h>
#include <Adafruit_Sensor.h>
#include <Adafruit_BME280.h>
#include <ArduinoJson.h>


#define BME280_ADRESA (0x76) // nastavení adresy senzoru

IPAddress IP(169,254,250,149); // adresa serveru
unsigned int localUdpPort = 2807;  // port

const char* ssid = "IoT";
const char* password = "raspberry";

char incomingPacket[255];  // buffer for incoming packets
char  replyPacekt[] = "Hi there! Got the message :-)";  // a reply string to send back

Adafruit_BME280 bme; // inicializace senzoru BME z knihovny

WiFiUDP Udp;

int LED_green = D3; 
int LED_white = D4; 
int LED_red = D0; 

int btn_LED_green = D7;
int btn_LED_white = D6;
int btn_LED_red = D5;

int FlameDetectionPin = D8;

int i =0;

int FlameDetection_value;

unsigned long aktualniMillis = 0; //aktualni cas
unsigned long predchoziMillis = 0; //cas poseldni akce

int lastButtonState = 0;
int lastButtonState1 = 0;
int lastButtonState2 = 0;

int lastFlameDetectionState = 0;

void setup()
{
  Serial.begin(115200);
  Serial.println();

  Serial.printf("Connecting to %s ", ssid);
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED)
  {
    delay(500);
    Serial.print(".");
  }
  Serial.println(" connected");

  Udp.begin(localUdpPort);
  Serial.printf("Now listening at IP %s, UDP port %d\n", WiFi.localIP().toString().c_str(), localUdpPort);

  // TODO
  if (!bme.begin(BME280_ADRESA)) {
    Serial.println("BME280 senzor nenalezen, zkontrolujte zapojeni!");
    while (1);
  }

  // TODO registrace zařízení
  StaticJsonBuffer<200> jsonBuffer11;
  JsonObject& reg = jsonBuffer11.createObject();

  reg["Message"] = "register";
  reg["DeviceID"] = WiFi.macAddress();
  reg["DeviceIP"] = WiFi.localIP().toString();
  reg["Description"] = "BME280,LED";

  Udp.beginPacket(IP, localUdpPort);
  reg.printTo(Udp);
  Udp.endPacket();

  pinMode(FlameDetectionPin, INPUT);

  pinMode(LED_green, OUTPUT);
  pinMode(LED_white, OUTPUT);
  pinMode(LED_red, OUTPUT);

  pinMode(btn_LED_green,INPUT_PULLUP);
  pinMode(btn_LED_white,INPUT_PULLUP);
  pinMode(btn_LED_red,INPUT_PULLUP);

}

void loop()
{

  int flameDetectionState = 1 - digitalRead(FlameDetectionPin);

  if (flameDetectionState != lastFlameDetectionState) {

    StaticJsonBuffer<200> jsonBuffer;
    JsonObject& root = jsonBuffer.createObject();

    root["Message"] = "sensorData";
    root["ArduinoID"] = WiFi.macAddress();
    root["sensor"] = "FlameDetection";

    JsonObject& data = root.createNestedObject("data");
    data.set("status", flameDetectionState ); 

    Udp.beginPacket(IP, localUdpPort);
    root.printTo(Udp);
    Udp.endPacket();

    lastFlameDetectionState = flameDetectionState; 
  }

  int buttonState = 1 - digitalRead(btn_LED_green);

  if (buttonState != lastButtonState) {

    if (buttonState == 1) { 

      Serial.println("btn 1");
      switchLight("btn_LED_green");
    }
    
    lastButtonState = buttonState;
  }

  int buttonState1 = 1 - digitalRead(btn_LED_white);

  if (buttonState1 != lastButtonState1) {
    
    if (buttonState1 == 1) { 

      Serial.println("btn 2");
      switchLight("btn_LED_white");
    }
    
    lastButtonState1 = buttonState1;
  }

  int buttonState2 = 1 - digitalRead(btn_LED_red);

  if (buttonState2 != lastButtonState2) {

    if (buttonState2 == 1) { 

      Serial.println("btn 3");
      switchLight("btn_LED_red"); 
    }

    lastButtonState2 = buttonState2;
  }

  int packetSize = Udp.parsePacket();
  if (packetSize){
    
    // receive incoming UDP packets
    //Serial.printf("Received %d bytes from %s, port %d\n", packetSize, Udp.remoteIP().toString().c_str(), Udp.remotePort());
    int len = Udp.read(incomingPacket, 255);

    // char JSONMessage[] = " {\"Sensor\": \"LED_green\", \"Value\": 1}"; 
     
    if (len > 0)
    {
      incomingPacket[len] = 0;
    }
    
    //Serial.printf("UDP packet contents: %s\n", incomingPacket);

    StaticJsonBuffer<300> JSONBuffer;   //Memory pool
    JsonObject& parsed = JSONBuffer.parseObject(incomingPacket); //Parse message
 
    const char * sensorType = parsed["Sensor"]; //Get sensor type value
    int value = parsed["Value"];      

    //Serial.println(sensorType);
    //Serial.println(value);
      
    if(strcmp (sensorType,"LED_green") == 0){

      analogWrite(LED_green, value);
      
    }

    if(strcmp (sensorType,"LED_white") == 0){

      analogWrite(LED_white, value);
      
    }

    if(strcmp (sensorType,"LED_red") == 0){

      analogWrite(LED_red, value);
      
    }
  }

  aktualniMillis = millis(); //aktualni cas

  if(aktualniMillis - predchoziMillis > 5000){

    predchoziMillis = aktualniMillis;
  
    if(!isnan(bme.readTemperature())){

      StaticJsonBuffer<200> jsonBuffer;
      JsonObject& root = jsonBuffer.createObject();

      root["Message"] = "sensorData";
      root["ArduinoID"] = WiFi.macAddress();
      root["sensor"] = "BME280";

      JsonObject& data = root.createNestedObject("data");
      data.set("temperature", bme.readTemperature()); // výpis teploty
      data.set("humidity", bme.readHumidity()); // výpis relativní vlhkosti
      data.set("pressure", bme.readPressure() / 100.0F);  // výpis tlaku s přepočtem na hektoPascaly

      Udp.beginPacket(IP, localUdpPort);
      root.printTo(Udp);
      Udp.endPacket();
  
    }
  }
  
}

//...................................Flame detection...................................



void FlameDetection_setup() {

  pinMode(FlameDetectionPin, INPUT);
}

void FlameDetection_loop() {

  FlameDetection_value = 1 - digitalRead(FlameDetectionPin);

}

void switchLight(String sensor){

    StaticJsonBuffer<200> jsonBuffer1;
    JsonObject& root1 = jsonBuffer1.createObject();

    root1["Message"] = "sensorData";
    root1["ArduinoID"] = WiFi.macAddress();
    root1["sensor"] = sensor;

    JsonObject& data1 = root1.createNestedObject("data");
    data1.set("status", 1 ); 

    Udp.beginPacket(IP, localUdpPort);
    root1.printTo(Udp);
    Udp.endPacket();

    Serial.println("btn");

}

```


- **Raspberry Pi** - Výhodná sada Raspberry Pi 3, 16GB karta, chladič, 2.5A zdroj, Onenine, černá [e-shop](http://rpishop.cz/raspberry-pi-sady/299-raspberry-pi-3-vyhodna-sada-krabicka-onenine.html)


### Zdroje
- [1] https://cs.wikipedia.org/wiki/Arduino
