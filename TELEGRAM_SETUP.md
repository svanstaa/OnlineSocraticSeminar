# Telegram Bot Setup für Themenvorschläge

## 1. Telegram Bot erstellen

1. Öffne Telegram und suche nach `@BotFather`
2. Starte einen Chat mit dem BotFather
3. Sende `/newbot` und folge den Anweisungen
4. Wähle einen Namen für den Bot (z.B. "Bitcoin Socratic Suggestions Bot")
5. Wähle einen Username (z.B. "bitcoin_socratic_suggestions_bot")
6. Kopiere den **Bot Token** (sieht aus wie: `1234567890:ABCdefGHIjklMNOpqrsTUVwxyz`)

## 2. Bot zu deinem Kanal hinzufügen

1. Gehe zu deinem Telegram-Kanal "Online Socratic Seminar"
2. Klicke auf den Kanalnamen → "Manage Channel" → "Administrators"
3. Klicke "Add Admin" und suche nach deinem Bot-Username
4. Füge den Bot als Administrator hinzu mit der Berechtigung "Post Messages"

## 3. Chat ID ermitteln

### Methode A: Mit @username_to_id_bot
1. Suche nach `@username_to_id_bot` in Telegram
2. Sende den Username deines Kanals (z.B. `@OnlineSocraticSeminar`)
3. Der Bot gibt dir die Chat ID zurück (beginnt mit `-100` für Kanäle)

### Methode B: Über Telegram API
1. Sende eine Testnachricht in deinen Kanal
2. Öffne: `https://api.telegram.org/bot<BOT_TOKEN>/getUpdates`
3. Ersetze `<BOT_TOKEN>` mit deinem Bot Token
4. Suche in der Antwort nach deiner Nachricht und kopiere die `chat.id`

## 4. Umgebungsvariablen setzen

### Für Netlify (Empfohlen):
1. Gehe zu deiner Netlify Site → "Site settings" → "Environment variables"
2. Füge hinzu:
   - `TELEGRAM_BOT_TOKEN`: Dein Bot Token
   - `TELEGRAM_CHAT_ID`: Die Chat ID deines Kanals (z.B. `-1001234567890`)

### Für lokale Entwicklung:
Erstelle eine `.env` Datei im Projektroot:
```
TELEGRAM_BOT_TOKEN=1234567890:ABCdefGHIjklMNOpqrsTUVwxyz
TELEGRAM_CHAT_ID=-1001234567890
```

## 5. Testen

1. Gehe auf deine Website
2. Fülle das Themenvorschlag-Formular aus
3. Klicke "An Telegram-Kanal senden"
4. Überprüfe, ob die Nachricht in deinem Telegram-Kanal erscheint

## Troubleshooting

- **403 Forbidden**: Bot ist nicht Administrator im Kanal oder hat keine Post-Berechtigung
- **400 Bad Request**: Chat ID ist falsch (stelle sicher, dass sie mit `-100` beginnt für Kanäle)
- **401 Unauthorized**: Bot Token ist ungültig
- **Server Error**: Überprüfe die Umgebungsvariablen in Netlify

## Sicherheit

- Teile niemals deinen Bot Token öffentlich
- Der Bot Token sollte nur in Umgebungsvariablen gespeichert werden
- Überprüfe regelmäßig die Bot-Berechtigungen in deinem Kanal
