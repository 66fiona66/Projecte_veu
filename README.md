# Projecte Veu - Aplicació de Control per Veu

Aplicació d'escriptori desenvolupada amb Vue.js 3 i Electron que permet controlar la interfície mitjançant comandes de veu en català.

## 🎯 Propòsit

El projecte **act3vue** és una aplicació d'escriptori multiplataforma que combina tecnologies web modernes amb un contenedor Electron per oferir una experiència d'usuari amb control per veu. La funcionalitat principal és el component `VoiceCommander` que processa comandes vocals en català com "saluda", "ajuda", "Tema" i "Reset". 

## 🛠️ Tecnologia

| Tecnologia | Versió | Ús |
|------------|---------|-----|
| **Vue.js** | 3.5.21 | Framework reactiva d'interfície d'usuari |
| **Vuetify** | 3.10.1 | Biblioteca de components Material Design |
| **Electron** | 39.2.6 | Contenidor d'aplicació d'escriptori |
| **Pinia** | 3.0.3 | Gestió d'estat |
| **Vue Router** | 4.5.1 | Enrutament client-side |
| **Vite** | 7.1.5 | Eina de construcció i servidor de desenvolupament | [3](#0-2) 

## 📦 Instal·lació

Instal·la les dependències amb el teu gestor de paquets preferit:

```bash
# Amb npm
npm install -y
npm install

# Amb electron
npm install electron --save-dev

```

## 🚀 Ús

### Servidor de desenvolupament

Per iniciar el servidor de desenvolupament amb recàrrega automàtica:

```bash
npm run dev
```

L'aplicació serà accessible a `http://localhost:3000` [4](#0-3) 

### Construcció per producció

Per construir l'aplicació per a producció:

```bash
npm run build
```
Els fitxers es generaran a la carpeta `dist/` [5](#0-4) 

### Executar com a aplicació d'escriptori

Després de construir, executa l'aplicació d'escriptori:

```bash
npm run start
```
Això iniciarà l'aplicació en una finestra d'Electron. [6](#0-5) 

## 🎤 Comandes de Veu

L'aplicació reconeix les següents comandes en català:

- **"saluda"** - Mostra un missatge de benvinguda
- **"ajuda"** - Mostra informació d'ajuda
- **"Tema"** - Canvia entre tema clar i fosc
- **"Reset"** - Restableix l'estat inicial de la interfície

El reconeixement de veu utilitza l'API Web Speech del navegador configurada per a català (`ca-ES`). [7](#0-6) 

## 📁 Estructura del Projecte

```
act3vue/
├── main.js                    # Procés principal d'Electron
├── src/
│   ├── main.js               # Arrencada de l'aplicació Vue
│   ├── App.vue               # Component arrel
│   ├── components/           # Components auto-importats
│   │   ├── VoiceCommander.vue    # Control per veu
│   │   └── ...
│   ├── composables/          # Funcions reutilitzables
│   │   └── useSpeechRecognition.js  # API de reconeixement de veu
│   ├── pages/                # Pàgines amb enrutament automàtic
│   └── plugins/              # Configuració de plugins Vue
├── package.json              # Dependències i scripts
└── vite.config.js            # Configuració de Vite
```

## 🔧 Característiques Destacades

- **Auto-importació**: Components i APIs de Vue s'importen automàticament
- **Enrutament basat en fitxers**: Les rutes es generen automàticament des de `src/pages/`
- **Reconeixement de veu en català**: Integració nativa amb l'API Web Speech
- **Tema adaptable**: Canvi entre mode clar i fosc per veu


### Citations

**File:** package.json (L1-6)
```json
{
  "name": "act3vue",
  "private": true,
  "type": "module",
  "version": "0.0.0",
  "main": "main.js",
```

**File:** package.json (L8-8)
```json
    "start": "electron .",
```

**File:** package.json (L9-9)
```json
    "dev": "vite",
```

**File:** package.json (L10-10)
```json
    "build": "vite build",
```

**File:** package.json (L14-22)
```json
  "dependencies": {
    "@fontsource/roboto": "5.2.7",
    "@mdi/font": "7.4.47",
    "electron": "^39.2.6",
    "pinia": "^3.0.3",
    "vue": "^3.5.21",
    "vue-router": "^4.5.1",
    "vuetify": "^3.10.1"
  },
```

**File:** src/components/VoiceCommander.vue (L21-39)
```vue
  if (command.includes('saluda')) {
    uiMessage.value = "Hola! Benvingut a l'aplicació.";
    statusColor.value = "success";
    alert("Hola!");
  }
  else if (command.includes('ajuda')) {
    uiMessage.value = "Aquesta és una prova de concepte.";
    statusColor.value = "info";
  }
  else if (command.includes('Tema')) {

    uiMessage.value = "CANVIO DE TEMA";
    theme.toggle()
  }
  else if (command.includes('Reset')) {
    uiMessage.value = "Reset";
    statusColor.value = ref("primary");

  }
```

**File:** src/composables/useSpeechRecognition.js (L19-21)
```javascript
  recognition.lang = 'ca-ES'; 
  recognition.continuous = false; // S'atura després d'una frase
  recognition.interimResults = true; // IMPORTANT: Permet veure resultats parcials
```

**File:** README.md (L1-4)
```markdown
# Vuetify (Default)

This is the official scaffolding tool for Vuetify, designed to give you a head start in building your new Vuetify application. It sets up a base template with all the necessary configurations and standard directory structure, enabling you to begin development without the hassle of setting up the project from scratch.

```

**File:** README.md (L76-79)
```markdown
## 📑 License
[MIT](http://opensource.org/licenses/MIT)

```


