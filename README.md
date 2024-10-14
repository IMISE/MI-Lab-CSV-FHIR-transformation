# MI-Lab-CSV-FHIR-transformation
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
### Mirth-connect mit Docker
**Wichtig:** Docker Desktop muss gestartet sein damit mit Docker gearbeitet werden kann. 
1. Clone GitHub Repository in neuen Ordner: `git clone https://github.com/IMISE/MI-Lab-CSV-FHIR-transformation.git`
2. Navigiere zum root Ordner "MI-Lab-CSV-FHIR-transformation" mit der Datei "docker-compose.yml"
3. Öffne den Terminal in diesem Ordner
4. Führe den Befehl `docker-compose up -d` aus
   Das zieht alle Docker images von einem Server. Der Download dauert ca. 5 min.
   In Docker Desktop sieht es dann folgendermaßen aus:
   ![docker5](https://github.com/user-attachments/assets/d6a2e65d-983c-4f7c-8e6e-995120973f7b)
   Dann wurden folgende Container im Docker-compose Netzwerk gestartet:
   - **Mirth Connect** mit eigener Postgres Datenbank
   - **Hapi FHIR Server** mit eigener Postgres Datenbank





