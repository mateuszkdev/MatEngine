# MatEngine - Discord.js Framework 

## Ważne link
* [Discord.js](https://discord.js.org/#/docs/main/stable/general/welcome) - Dokumentacja discord.js 
* [Node.js](https://nodejs.org/en/) - Node.js, narzędzie potrzebne do uruchomienia bota
* [Serwer Discord](https://discord.gg/JffNufb) - Wszelkie odpowiedzi na pytania

## Instalacja
Postępuj zgodne z punktami:

1. Sklonuj plik core do folderu bota.
2. Upewnij się że masz zainstalowane NODE.JS
3. Uruchom wiersz poleceń w danym folderze
4. Zainstaluj discord.js
    ```
    $ npm install discord.js 
    ```
5. Utwórz plik bota
6. Zaimportuj core 
    ```js
    const { core } = require('./MatEngine')
    ```
7. Stwórz nowa klase na bazie core i zacznij działać!

## Informacje

* Wersja Frameworku: **v.1.0.0**
* Framework dzała na podstawie licencji.

# Zastosowanie w praktyce

## Deklaracja client'a

```js
const bot = new core({

    /* CLIENT_TOKEN - token naszego bota */
    CLIENT_TOKEN: token,

    /* 
    PLUGINS_FOLDER - folder na komendy ( musi zawierać folery jako kategori)
    EVENTS_FOLDER - folder na wydarzenia ( musi zawerać foldery do podzialu )
    */
    PLUGINS_FOLDER: './plugins',
    EVENTS_FOLDER: './events',

    /* 
    MESSAGE_EMBED: - konfiguracja wiadomości typu embed jakie będzie wysyłać bot
        CORRECT_COLOR: kolor embedu przy poprawnym wykonaniu komendy
        ERROR_COLOE: kolor embedu w wypadku błędu
    */
    MESSAGE_EMBED: {
        CORRECT_COLOR: '#17E742',
        ERROR_COLOR: '#E71724'

    },

    /*
    GROUPS: jako uprawnienia do komendy, możemy podać w komedzie permissje, lub grupe zdefiniowaną tutaj. Przykładowe grupy:
    */
    GROUPS: {

        'admin': ['ADMINISTRATOR'],
        'moderator': ['KICK_MEMBERS', 'BAN_MEMBERS'],
        'helper': ['MANAGE_MESSAGES']

    },

    /* PREFIX bota */
    PREFIX: 'hi ',

    /* Kod weryfikacji naszej licencji na framework */
    VERIFY_CODE: 'A3V2A1',

    /* USER_DATA - obiekt da użytkownika, można z niego korzysać puźniej w komandach */
    USER_DATA: {

        hi: 'Niesamowite'

    },

    // Język wykonawczy frameworku
    BASIC_LANG: 'PL'

})
````

<br><br>

## Przykład komendy
    ./plugins/basic/ping.js

Przykładowe wykonanie komendy **ping** z użyciem framework'u

```js
module.exports = {

    name: 'ping',
    aliases: ['pong', 'ping-pong'],
    category: 'basic',

    run: (data) => {

        return {

            text: 'Ping? Pong!',
            title: 'Ping pong...'

        }

    }

}
```
Powyższy kod, po wpisanu ( zakładając prefix jako ! ) !ping, zwróci wiadomość typu embed z tytułem **Ping pong..** oraz *description* **Ping? Pong!**

Jeżeli byś my chcieli zwykłą wiadomość, piszemy:
```js
return {

    text: 'Ping? Pong!',
    message: true

}
```

Atrybut **message: true** przekazuje informacje że chcemy wysłać samą wiadomość.

<br><br>

## Przykładowy event
    ./events/bin/ready.js
Przykładowy plik eventu **ready.js**
```js
module.exports = (client) => {

    console.log(`Zalogowano jako ${client.user.tag}`)

}
```

### **UWAGA**
Deklarowanie tego, jaki event znajduje się w jakim pliku, określamy poprzez **NAZWĘ PLIKU**
