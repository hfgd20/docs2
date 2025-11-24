# Architecture

hfg.design 2.0 ist eine intelligente Lehr- und Lernplattform, die aus mehreren spezialisierten Core-Services besteht. Die Architektur ist darauf ausgelegt, nahtlose Kollaboration, Live-Streaming und AI-gestützte Inhaltsanalyse zu ermöglichen.

![Architekturdiagramm](/images/architecture.png)

## System-Übersicht

Das zentrale Element unserer Anwendung bildet die **[UI](ui)** - unsere Vue.js-Webanwendung von hfg.design 2.0. Sie stellt eine einheitliche Benutzeroberfläche für alle Systemfunktionen bereit und integriert seamless verschiedene Arbeitsräume (Spaces) mit unterschiedlichen Capabilities.

Die **[API](api)** fungiert als zentraler Vermittler und verwaltet alle persistenten Daten über eine RESTful-Schnittstelle. Sie koordiniert die Kommunikation zwischen allen Services und bietet Real-time-Updates über Socket.io.

## Core Services

### Datenhaltung & Storage

**[MongoDB](mongodb)** - Unsere zentrale NoSQL-Datenbank speichert alle Anwendungsdaten:

- **Spaces** mit verschiedenen Typen (COURSE, CHANNEL, DM, PROJECT_GROUP, etc.)
- **Capability-basierte Konfiguration** (CHAT, STREAM, VOD, FILES, etc.)
- **User-Profile** mit erweiterten Attributen und Berechtigungssystem
- **AI-Ergebnisse** wie OCR-Texte, Objekterkennung und Slide-Metadaten

**[MinIO](minio)** - S3-kompatibles Object Storage für Mediendateien:

- **Slide-Screenshots** automatisch erfasst von AI-Agents
- **Space- und User-Avatare** mit flexibler Zugriffskontrolle
- **Automatische Bereinigung** ungenutzter Assets

### Kommunikation & Collaboration

**[Matrix Synapse](synapse)** - Unser Chat-Backend ermöglicht:

- **End-to-End-Verschlüsselung** mit aktueller Schlüsselsynchronisation
- **Integration mit Live-Streams** für Kommentare auf Folien
- **Flexible Raum-Strukturen** passend zu Space-Konfigurationen

**[LiveKit](livekit)** - WebRTC-Plattform für Live-Übertragungen:

- **Bildschirmfreigabe** optimiert für Vorlesungsfolien
- **Interaktive Tools** für Live-Kommentare und Textmarkierungen
- **AI-Agent-Integration** für automatische Stream-Analyse
- **Skalierbare Infrastruktur** für große Vorlesungen

### Authentifizierung & Sicherheit

**[Keycloak](keycloak)** - Zentrales Identity & Access Management:

- **Multi-Client-Authentifizierung** (PKCE für UI, Client-Credentials für Services)
- **User-Discovery** für Einladungs- und Kollaborationsfunktionen
- **Single Sign-On** für alle Systemkomponenten
- **Feingliedrige Berechtigungskontrolle** je nach Space-Typ

### Intelligente Inhaltsanalyse

**[AI-Agents](ai)** - Spezialisierte Agents für automatisierte Stream-Analyse:

- **Agent-Coordinator**: Zentrale Steuerung aller AI-Prozesse
- **Agent-Slidechange**: Automatische Erkennung von Folienwechseln
- **Agent-OCR**: Texterkennung mit Bounding-Box-Koordinaten
- **Agent-YOLO**: Objekterkennung auf Vorlesungsfolien
- **Agent-Summarize**: LLM-basierte Inhaltszusammenfassungen
- **Agent-STT**: Speech-to-Text für Barrierefreiheit

## Datenfluss & Integration

1. **Live-Streams** werden über LiveKit übertragen
2. **AI-Agents** analysieren Inhalte in Echtzeit und erstellen Screenshots
3. **Medien** werden in MinIO gespeichert, **Metadaten** in MongoDB
4. **OCR- und YOLO-Ergebnisse** werden direkt in Slide-Dokumenten eingebettet
5. **Real-time-Updates** synchronisieren alle Änderungen über die API an UI-Clients
6. **Chat-Integration** ermöglicht Diskussionen parallel zu Streams
7. **Highlight-System** erlaubt persistente Markierungen auf Folien

## Technologiestack

- **Frontend**: Vue.js mit Nuxt.js
- **Backend**: Express.js REST-API mit Socket.io
- **Datenbank**: MongoDB mit Typegoose
- **Storage**: MinIO S3-kompatibel
- **Streaming**: LiveKit WebRTC
- **Chat**: Matrix Synapse
- **Auth**: Keycloak OpenID Connect
- **AI**: Selbst gehostete Modelle auf NVIDIA Tesla

Die Architektur kombiniert moderne Webtechnologien mit spezialisierter AI-Hardware, um eine intelligente und skalierbare Lehr- und Lernumgebung zu schaffen.
