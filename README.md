# Integracja Slack z Google Calendar przez n8n i MCP

Projekt zawierający implementację integracji notatek głosowych ze Slacka z Google Calendar za pomocą n8n i protokołu MCP (Model Context Protocol).

## Opis projektu

System pozwala na automatyczne przetwarzanie notatek głosowych ze Slacka, analizowanie ich treści, klasyfikowanie jako wydarzenia zawodowe, prywatne lub rodzinne, a następnie dodawanie ich do odpowiedniego kalendarza Google. Dodatkowo, system wykrywa potencjalnych uczestników wydarzenia i wysyła im zaproszenia e-mail.

## Główne funkcjonalności

1. Odbieranie powiadomień o notatkach głosowych ze Slacka przez webhook
2. Ekstrakcja tekstu z notatek głosowych (lub wiadomości tekstowych)
3. Analiza treści i kategoryzacja wydarzenia (praca/prywatne/rodzina)
4. Wykrywanie daty i godziny wydarzenia z tekstu
5. Identyfikacja adresów e-mail uczestników wydarzenia
6. Tworzenie wydarzenia w odpowiednim kalendarzu Google
7. Wysyłanie zaproszeń e-mail do uczestników

## Komponenty projektu

- **n8n Workflow** - główny komponent automatyzacji, który przetwarza dane i wykonuje operacje
- **MCP Server** - serwer MCP umożliwiający zarządzanie workflow przez Claude
- **Slack App** - aplikacja Slack, która wysyła powiadomienia do webhooka n8n
- **Google Calendar API** - API wykorzystywane do dodawania wydarzeń w kalendarzu
- **Gmail API** - API używane do wysyłania zaproszeń e-mail

## Wymagania

- Node.js (v14+)
- n8n (instancja lokalna lub cloudowa)
- Dostęp do API Slack
- Dostęp do API Google (Calendar i Gmail)
- Claude Desktop (dla integracji MCP)

## Pliki w repozytorium

- `create_n8n_workflow.js` - skrypt tworzący workflow w n8n
- `activate_workflow.js` - skrypt aktywujący workflow (rozwiązanie problemu HTTP 405)
- `n8n_mcp_server.js` - implementacja serwera MCP dla n8n
- `claude_desktop_config.json` - przykładowa konfiguracja Claude Desktop
- `slack_app_config.md` - instrukcje konfiguracji aplikacji Slack

## Rozwiązane problemy

- Problem z metodą HTTP 405 podczas aktywacji workflow przez API
- Niezgodność formatu danych między API n8n a MCP
- Problemy z autentykacją i autoryzacją API

## Autorzy

- Projekt utworzony przy wsparciu Claude 3.7 Sonnet

## Licencja

MIT