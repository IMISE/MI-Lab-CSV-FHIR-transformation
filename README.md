# MI-Lab-CSV-FHIR-transformation

Dieses Repository enthält die Übungsmaterialien für die MI-Lab Übung 2 zum Thema **Transformation von CSV nach FHIR** mit [Mirth-Connect](https://www.nextgen.com/solutions/interoperability/mirth-integration-engine)
und [Hapi FHIR](https://hapifhir.io/).

## Inhaltsverzeichnis
1. [Docker Installation](#docker-installation)
2. [Docker-Compose](#docker-compose)
3. [Mirth-Connect Installation](#mirth-connect-installation)
4. [Docker Netzwerk mit Mirth-Connect](#docker-netzwerk-mit-mirth-connect)
5. [Mirth-Connect Ordnerstruktur](#mirth-connect-ordnerstruktur)

**Vorraussetzungen:** Docker mit Docker-compose, Java

## Docker Installation
### Docker Desktop
Docker Desktop [Download](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=dd-smartbutton&utm_location=module) (Windows) 
Für andere Betriebssysteme siehe [Docker](https://www.docker.com/products/docker-desktop/)
**Wichtig:** Die Installation startet einmal den Rechner neu
1. Configuration
  ![docker1](https://github.com/user-attachments/assets/4df34253-41c2-4a82-86cc-b8016bbac017)
  ![docker2](https://github.com/user-attachments/assets/9b3e3b0b-7084-49f3-9f9c-22a915e6e97b)
2. Ohne Anmeldung fortfahren
   Klicke "Skip" um ohne Anmeldung Docker Desktop zu benutzen 
   ![docker3](https://github.com/user-attachments/assets/e51ec963-5a34-40dc-88cd-7156395b49e5)
3. Installation abgeschlossen
   ![docker4](https://github.com/user-attachments/assets/181e767a-9ea1-43a7-855d-a804a72ee707)

### Docker-Compose
**Wichtig:** Docker Desktop muss gestartet sein damit mit Docker gearbeitet werden kann. 
1. Clone GitHub Repository in neuen Ordner: `git clone https://github.com/IMISE/MI-Lab-CSV-FHIR-transformation.git`
2. Navigiere vom root Ordner "MI-Lab-CSV-FHIR-transformation" in den "Setup" Ordner mit der Datei "docker-compose.yml"
3. Öffne den Terminal in diesem Ordner
4. Führe den Befehl `docker-compose up -d` aus
   Das zieht alle Docker images von einem Server. Der Download dauert ca. 5 min.
   In Docker Desktop sieht es dann folgendermaßen aus:
   ![docker5](https://github.com/user-attachments/assets/d6a2e65d-983c-4f7c-8e6e-995120973f7b)
  
### Mirth-Connect Installation
1. Im Browser ´localhost:8080´ aufrufen
   Oder über Docker Desktop aufrufen siehe:
   ![docker7GIF](https://github.com/user-attachments/assets/9a5c6943-7c36-4771-bf29-6eae11f62833)
2. Klicken Sie auf **Download Administrator Launcher**
3. Installieren Sie die heruntergeladene Datei "mirth-administrator-launcher-latest-windows"

## Docker Netzwerk mit Mirth-Connect 
Für diese Übung werden verschiedene Anwendungen benötigt, die als Docker Container über ein Netzwerk zusammen geschaltet sind. 
Mit Hilfe von [Docker-Compose](https://docs.docker.com/compose/) können mit nur einem Befehl alle benötigten Container gestartet werden.

Folgende Container (Anwendungen) sind nach dem [Starten](#docker-compose) von Docker-Compose online:
| Container | Ports | Volumes | Grund |
| -------- | ------- | ------- | ------- |
| Mirth-Connect | **8080**, 8443 | Ordner: /Setup/mirth-connect/ | Hauptanwendung |
| Mirth-Connect Database | 5434 || Datenbank für Speicherung von Mirth-Connect |
| Hapi FHIR | **8090** || Hapi FHIR Server an dem die finalen gemappten FHIR Ressourcen gesendet werden |
| Hapi FHIR Database| 5433 || Datenbank für Speicherung von Hapi FHIR |
| ClinFHIR | **8000** || Browseranwendung zur graphischen Veranschauung von FHIR Daten |

## Mirth-Connect Ordnerstruktur
In der Übung soll Mirth-Connect auf die CSV-Dateien in einem definierten Ordner zugreifen und diese einlesen. Da Mirth-Connect abgekapselt in einem
Docker Container läuft, wurde ein Ordner im Container auf einen lokalen Ordner im Computer gemappt. 
Weitere Informationen dazu sind in der Docker Dokumentation zu [Volumes](https://docs.docker.com/engine/storage/volumes/).

**Docker Container Ordner**: /opt/connect/appdata 

**Lokaler Ordner**: [/Setup/mirth-connect](https://github.com/IMISE/MI-Lab-E02-CSV-to-FHIR/tree/main/Setup/mirth-connect)

**Wichtig:** Nur Dateien und Unterordner in dem Ordner **/Setup/mirth-connect** werden von Mirth-Connect erkannt. 

