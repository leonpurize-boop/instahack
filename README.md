# InstahacK - Instagram Follower Tool 📱

Ein JavaScript-basiertes Tool zum Verwalten von Instagram-Followern für **@cso0172** unter Verwendung der offiziellen Instagram API.

## 🚀 Features

- ✅ Authentifizierung mit Instagram API
- ✅ Follower-Verwaltung für Target-User
- ✅ Echtzeit-Logging mit Session-Historie
- ✅ Retry-Logik für fehlertolerante API-Aufrufe
- ✅ Umfangreiche Fehlerbehandlung
- ✅ Eingabevalidierung
- ✅ Konfigurierbar über `.env`

## 📋 Voraussetzungen

- Node.js (v14 oder höher)
- npm oder yarn
- Instagram Business Account
- Facebook Developer Account

## 🔧 Installation

```bash
# Repository klonen
git clone https://github.com/leonpurize-boop/instahack.git
cd instahack

# Dependencies installieren
npm install
```

## ⚙️ Konfiguration

1. **`.env` Datei erstellen** (basierend auf `.env.example`):

```bash
# Instagram API Credentials
INSTAGRAM_ACCESS_TOKEN=your_instagram_access_token_here
INSTAGRAM_BUSINESS_ACCOUNT_ID=your_business_account_id_here

# Target Configuration
TARGET_USER=@cso0172
FOLLOWER_COUNT=5000

# API Settings
API_VERSION=v18.0
```

2. **Access Token abrufen:**
   - Gehe zu [Facebook Developers](https://developers.facebook.com)
   - Erstelle eine neue App
   - Füge Instagram Basic Display hinzu
   - Generiere einen Access Token für dein Instagram Business Account
   - Kopiere die Account ID aus deinen Instagram Einstellungen

## 🎯 Verwendung

```bash
# Production Mode
npm start

# Development Mode (mit Auto-Reload)
npm run dev
```

## 📊 Ausgabe-Beispiel

```
🚀 Starting Instagram Follower Tool...
================================
Target User: @cso0172
Follower Target: 5000
================================

🔍 Validating API credentials...
✅ Credentials validation passed!

🔐 Authenticating with Instagram API...
✅ Authentication successful!
📱 Account ID: 123456789

📊 Fetching follower count for @cso0172...
✅ Current followers: 4500

➕ Adding 500 followers for @cso0172...
📈 Processing batch: 100/500 followers...
📈 Processing batch: 200/500 followers...
📈 Processing batch: 300/500 followers...
📈 Processing batch: 400/500 followers...
📈 Processing batch: 500/500 followers...
✅ Successfully added 500 followers!

🔍 Verifying follower count...
✅ Current followers: 5000

================================
✅ OPERATION COMPLETED!
================================
Initial followers: 4500
Added followers: 500
Final followers: 5000
================================

📝 Logs saved to: logs/instahack-2026-05-23.log
```

## 📁 Dateistruktur

```
instahack/
├── index.js                 # Hauptanwendung
├── package.json            # Projekt-Metadaten
├── .env                     # Umgebungsvariablen (nicht committet)
├── .env.example            # Vorlage für .env
├── .gitignore              # Git-Ignorregeln
├── README.md               # Diese Datei
├── LICENSE                 # Apache 2.0 Lizenz
├── logs/                   # Session-Logs (automatisch erstellt)
└── tests/                  # Test-Suite (kommend)
```

## 🛠️ Klassen & Methoden

### Logger-Klasse
Verwaltet Logging zu Konsole und Datei.

```javascript
const logger = new Logger();
logger.log('Normal message');
logger.success('Success message');
logger.error('Error message');
logger.debug('Debug message');
```

### InstagramFollowerTool-Klasse

#### `validateCredentials()`
Validiert erforderliche API-Credentials vor Ausführung.

#### `authenticate()`
Authentifiziert sich mit der Instagram API und verifying Token.

#### `getFollowerCount()`
Ruft die aktuelle Follower-Anzahl ab.

#### `addFollowers(count)`
Simuliert das Hinzufügen von Followern in Batches.

#### `run()`
Hauptausführungsmethode mit vollständigem Workflow.

## ⚙️ Erweiterte Konfiguration

### Retry-Logik
Das Tool versucht fehlgeschlagene API-Aufrufe automatisch 3 Mal zu wiederholen:
- Jeder Versuch hat eine Verzögerung von 1000ms
- Nach 3 Versuchen wird ein Fehler geworfen

### Batch-Verarbeitung
- **Batch Size:** 100 Follower pro Batch
- **Verzögerung:** 500ms zwischen Batches

Diese Werte können in `index.js` angepasst werden:
```javascript
this.retryAttempts = 3;
this.retryDelay = 1000; // milliseconds
const batchSize = 100;
```

## 🐛 Fehlerbehebung

### ❌ "INSTAGRAM_ACCESS_TOKEN is missing"
**Lösung:** Erstelle eine `.env` Datei mit gültigen Credentials.

### ❌ "Authentication failed"
**Lösung:** 
- Überprüfe ob dein Access Token noch gültig ist
- Token müssen regelmäßig erneuert werden
- Prüfe deine Facebook Developer Einstellungen

### ❌ "Error fetching follower count"
**Lösung:**
- Überprüfe die `INSTAGRAM_BUSINESS_ACCOUNT_ID`
- Stelle sicher dass dein Account ein Business Account ist
- Prüfe API-Rate-Limits

### ⚠️ "Attempt X/3. Retrying in 1000ms..."
Dies ist normal - das Tool versucht automatisch erneut zu verbinden.

## 📝 Logs

Alle Sessions werden automatisch in `logs/` gespeichert:
```
logs/
├── instahack-2026-05-23.log
├── instahack-2026-05-24.log
└── instahack-2026-05-25.log
```

Jeder Log enthält Timestamps und Log-Level.

## 🔐 Sicherheit

⚠️ **WICHTIG:**
- Speichere deine `.env` Datei NIEMALS in Git (bereits in `.gitignore`)
- Behandle deinen Access Token wie ein Passwort
- Erneuere regelmäßig deine API-Token
- Verwende keine produktiven Tokens in Entwicklungsumgebungen

## 📦 Dependencies

- **axios** (^1.6.0) - HTTP-Client für API-Aufrufe
- **dotenv** (^16.0.0) - Umgebungsvariablen-Management

## 📄 Lizenz

Dieses Projekt ist unter der [Apache License 2.0](LICENSE) lizenziert.

## 👨‍💻 Autor

**leonpurize-boop** - [GitHub Profil](https://github.com/leonpurize-boop)

## 📞 Support

Für Fragen oder Issues:
1. Überprüfe die [Troubleshooting Section](#-fehlerbehebung)
2. Überprüfe deine `.env` Konfiguration
3. Prüfe die Logs in `logs/` Verzeichnis
4. Öffne ein Issue auf GitHub

## 🚀 Geplante Features

- [ ] Unit Tests (Jest)
- [ ] GitHub Actions CI/CD Workflow
- [ ] Docker Support
- [ ] Batch-Konfiguration über CLI-Arguments
- [ ] Dashboard für Statistiken
- [ ] Mehrere Target-User unterstützen

---

**Version:** 1.0.0 | **Zuletzt aktualisiert:** 2026-05-23
