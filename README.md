🤖 AI Automation – n8n + Telegram + Ollama + ngrok

Dieses Projekt stellt eine komplette AI-Automation Umgebung mit folgenden Komponenten bereit:

🤖 n8n (Workflow Automation)
🧠 Ollama (lokales LLM – z.B. llama2)
🐘 PostgreSQL (n8n Datenbank)
🌐 ngrok (öffentlicher Webhook Zugang)
📩 Telegram Bot Integration

Der Workflow:
Telegram → n8n → Ollama → Telegram Antwort

📦 Architektur
Telegram
   │
   ▼
 n8n ─────► Ollama (LLM)
   │
   ▼
Telegram Antwort
Alle Services laufen in Docker Containern.

⚙️ Voraussetzungen
Docker
Docker Compose
Telegram Bot Token
ngrok Authtoken
🚀 Installation
1. Repository klonen
2. </> Bash: git clone https://github.com/DEIN_USERNAME/automation.git
cd automation

2. ngrok Token setzen

In ngrok.yml:
</>YAML
authtoken: YOUR_NGROK_TOKEN

3. Docker starten
docker-compose up -d
4. n8n öffnen
http://localhost:5678
🧠 Ollama Model installieren

Falls noch nicht vorhanden:

docker exec -it ollama ollama pull llama2
📥 Workflow importieren

Importiere die Datei:

projekt1.json

In n8n:

Workflow → Import → Datei auswählen
🔄 Workflow Beschreibung

Dieser Workflow macht:

Telegram Nachricht empfangen
Nachricht an Ollama senden
AI Antwort generieren
Antwort zurück an Telegram senden
🐳 Services

Die Docker Compose Datei startet folgende Container:

postgres
n8n
ollama
ngrok

Die Services sind über ein internes Docker Netzwerk verbunden.

🌐 Webhook Zugriff über ngrok

ngrok erstellt eine öffentliche URL für Telegram Webhooks.
Konfiguration in:

ngrok.yml

📩 Telegram Bot

Der Workflow nutzt:

Telegram Trigger
HTTP Request zu Ollama
Telegram Send Message

Definition im Workflow JSON:

▶️ Start / Stop

Start:

docker-compose up -d

Stop:

docker-compose down

Logs:

docker-compose logs -f
🛠️ Anpassungen

Du kannst:

anderes Ollama Modell verwenden (mistral, llama3, etc.)
weitere n8n Automationen hinzufügen
zusätzliche APIs anbinden
AI Agent erweitern
📌 Beispiel

Telegram Nachricht:

Hallo AI

Antwort:

Hallo! Wie kann ich dir helfen?
🔐 Sicherheit Hinweis

Bitte vor Veröffentlichung:

ngrok Authtoken entfernen
Telegram Credentials entfernen
.env Datei verwenden
