
# NINAProject

NINAProject è un'applicazione che simula un sistema MQTT con tre componenti principali: NINAMock, nina_react e Mosquitto. 
Questa applicazione è progettata per interagire con un broker MQTT e visualizzare i messaggi in tempo reale tramite un'interfaccia React.

## Struttura del Progetto

- **NINAMock**: un mock che invia messaggi MQTT simulando il comportamento di N.I.N.A. Questo componente utilizza `paho-mqtt` per comunicare con il broker.
- **nina_react**: una web app frontend basata su React e Vite, che si connette al broker MQTT tramite WebSocket per ricevere e visualizzare i messaggi.
- **Mosquitto**: broker MQTT che gestisce le comunicazioni tra i client. È configurato per accettare connessioni WebSocket sulla porta 9001.

## Requisiti

- **Docker** e **Docker Compose**: assicurati di avere Docker e Docker Compose installati per eseguire tutti i servizi con un solo comando.

## Configurazione

### Mosquitto

Il broker Mosquitto è configurato per accettare connessioni WebSocket sulla porta 9001. Assicurati che il file `mosquitto.conf` sia presente nella cartella `Mosquitto` per il corretto funzionamento.

### NINAMock

NINAMock utilizza un file `config.json` per configurare il broker MQTT. Verifica che `config.json` sia presente nella stessa directory di `nina_mock.py` e contenga le seguenti informazioni:

```json
{
  "broker_address": "localhost",
  "topic": "your/topic"
}
```

### nina_react

nina_react è una web app basata su React e Vite che utilizza la libreria `mqtt` per connettersi al broker MQTT tramite WebSocket.

## Avvio del Progetto

Per eseguire NINAProject con Docker Compose, segui questi passaggi:

1. Assicurati che tutti i file necessari siano presenti, inclusi `Dockerfile`, `mosquitto.conf`, `config.json`, e `docker-compose.yml`.
2. Esegui il comando per avviare tutti i servizi:
   ```bash
   docker-compose up --build
   ```

3. Accedi alla web app su [http://localhost:3000](http://localhost:3000) per visualizzare l'interfaccia React.

## Struttura dei File

- `NINAMock`: contiene `nina_mock.py` e `config.json`.
- `nina_react`: contiene la web app React/Vite.
- `Mosquitto`: contiene `mosquitto.conf` per configurare il broker.

## Utilizzo

- **Invio di messaggi**: NINAMock invia messaggi al topic specificato, e questi vengono visualizzati in `nina_react`.
- **Connessione a WebSocket**: nina_react si connette automaticamente al broker tramite WebSocket per ricevere i messaggi in tempo reale.

## Risoluzione dei Problemi

- **Porta occupata**: Assicurati che le porte 1883 (MQTT) e 9001 (WebSocket MQTT) non siano occupate da altri servizi.
- **Errori di configurazione**: Verifica che `mosquitto.conf` e `config.json` siano configurati correttamente.
- **Connessione al broker**: Se nina_react non si connette, controlla che il broker sia in esecuzione e che la configurazione della porta WebSocket sia corretta.

## Contatti

Per ulteriori informazioni o assistenza, contatta @Aenigmos.