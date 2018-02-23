Firebase je platforma pro vývoj mobilních a webových aplikací vyvinutá firmou Firebase, Inc. v roce 2011 a poté získala společnost Google v roce 2014. [1]

### Instalace OS

1. **Registrace Google účtu** Abychom mohli plně využívat služeb Firebase, potřebujeme mít platný účet u společnosti Google, Inc. Pokud tento účet nemáme, budeme ho muset v prvé řadě vytvořit. [Registrace zde](https://accounts.google.com/SignUp?continue=https%3A%2F%2Fwww.google.cz%2F%3Fgfe_rd%3Dcr%26ei%3DUXnfWML0IfGv8wfVooPIAg&hl=cs)

2. **Vytvoření nového projektu** na stránkách [https://console.firebase.google.com/](https://console.firebase.google.com/) vytvořte nový projekt kliknutím na tlačítko *Add project*. V dalším kroku vyplňte potřebné údaje a nový projekt vytvořte stisknutím *CREATE PROJEKT*.

3. **Vytvoření nové aplikace pro platformu Android** 
  - Krok 1: Chceme-li využívat služeb Firebase v aplikacích na platformě Android, je potřeba pro každou takovouto aplikaci založit novou aplikaci pro platformu Android v nově založeném projektu. Vytvoříme ji liknutím na * Add Firebase to your Android app*. 
  - Krok 2: Následně je velmi důležité vyplnění kolonky Android *package name*. Název tohoto package najdeme v nově vytvořeném projektu Android Studia. Ve struktuře našeho projektu jej můžeme nalézt v .xml souboru s názvem AndroidManifest. V mém případě je zde uvedeno jako *package="com.example.liptel.raspberrypi"*. Jakmile máme package vyplněny, pokračujeme tlačítkem *REGISTER APP*.

  - Krok 3: Download google-services.json. Když máme soubor stažený, musíme jej přesunout do našeho projektu v Android Studiu. Nejjednodušší cesta, jak .json soubor do našeho projektu zkopírovat, je pomocí windows průzkumníka. Nejběžnější cesta je následující: C:\Users\user\AndroidStudioProjects\[název Android projektu]\app. Do této složky nakopírujeme náš .json soubor.


**Firebase Cloud Messaging**

Firebase Cloud Messaging (FCM) je řešení pro zasílání zpráv mezi platformami, které vám umožní spolehlivě doručovat zprávy zdarma.
Pomocí služby FCM můžete upozornit na aplikaci klienta, že jsou k synchronizaci k dispozici nová e-mailová nebo jiná data. Zprávy o oznámení můžete posílat, abyste mohli opětovně zapojit a uchovat uživatele. U aplikací, jako je například instant messaging, může zpráva přenést užitečné zatížení až 4 kB do aplikace klienta.

Používáte službu Google Cloud Messaging již nyní? Další informace o možnostech.





Ukládejte a synchronizujte data s naší databází cloud NoSQL. Data jsou synchronizována ve všech klientech v reálném čase a zůstávají k dispozici, když aplikace zmizí.
Firebase Realtime Database je databáze hostovaná v cloudu. Data jsou uložena jako JSON a synchronizována v reálném čase s každým připojeným klientem. Při vytváření aplikací s více platformami pomocí našich sady iOS, Android a JavaScript SDK sdílí všichni vaši klienti jednu instanci databáze Realtime a automaticky přijímá aktualizace s nejnovějšími daty.

[Guide zde](https://firebase.google.com/docs/database/)





1 https://en.wikipedia.org/wiki/Firebase
