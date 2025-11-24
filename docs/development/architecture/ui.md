# UI

## Einführung

Unsere UI ist das zentrale Element unseres Systems und bildet die Webanwendung von hfg.design 2.0. Sie stellt die Hauptschnittstelle dar, über die Studierende, Lehrende und andere Nutzer mit der gesamten Plattform interagieren. Die UI verbindet alle Backend-Services nahtlos miteinander und bietet eine einheitliche Benutzererfahrung für alle Funktionen der Lehr- und Lernplattform.

### Hauptmerkmale

- **Space-basierte Architektur**: Zentrale Arbeitsräume für Kommunikation und Kollaboration
- **Modulare Landing Page**: Personalisierbare Startseite mit anpassbaren Bausteinen
- **Integrierte Kommunikation**: Chat, Streams und Dateiaustausch in einer Umgebung
- **Responsive Design**: Optimiert für verschiedene Geräte und Bildschirmgrößen
- **Real-time Updates**: Live-Synchronisation aller Änderungen über Socket.io
- **Benutzerfreundliche Navigation**: Intuitive Sidebar und Suchfunktionen

### Rolle in der Architektur

Die UI fungiert als zentrale Steuerungseinheit des gesamten Systems:

- **Benutzeroberfläche**: Stellt alle Funktionen der Plattform in einer einheitlichen Oberfläche bereit
- **Space-Management**: Verwaltet Kurse, Channels, Direktnachrichten und Projektgruppen
- **Stream-Integration**: Eingebettete [LiveKit](livekit)-Streams für Vorlesungsübertragungen mit interaktiven Tools
- **Chat-Integration**: Nahtlose Einbindung des [Matrix Synapse](synapse)-Messaging-Systems
- **Datei-Verwaltung**: Direkter Zugriff auf [MinIO](minio)-Objektspeicher für Medien und Dokumente
- **Echtzeit-Synchronisation**: Live-Updates über [API](api) und Socket.io für alle Systemänderungen
- **Authentifizierung**: Single Sign-on über [Keycloak](keycloak) Integration

Mehr Details zum Funktionsumfang und Systemaufbau finden sich im [Systemaufbau](/) Teil unserer Dokumentation.
