# INFO
## Architecture globale
User Input  
↓  
Map + Footprint  
↓  
Plan overlay (PNG)  
↓  
Wall drawing  
↓  
Polygonization (units)  
↓  
Semantic enrichment  
↓  
Validation  
↓  
IMDF Export  


---

## Workflow utilisateur

### 1. Création du projet
- Saisie d’une adresse
- Géocodage → coordonnées GPS
---
### 2. Définition du bâtiment
- Affichage carte
- Dessin du footprint (polygone)
---
### 3. Ajout du plan (PNG)
- Upload image
- Positionnement :
  - translation
  - rotation
  - scale
---
### 4. Dessin des murs
- Mode "draw wall"
- Construction de segments
---
### 5. Génération automatique des pièces
- Polygonisation à partir des murs
- Détection des surfaces fermées
---
### 6. Ajout des ouvertures
- Placement de portes sur murs
- Orientation automatique
---
### 7. Enrichissement métier
- Attribution des catégories :
  - bureau
  - salle de réunion
  - WC
  - couloir
- Nommage des pièces
---
### 8. Gestion des niveaux
- Multi-étages
- Duplication / édition
---
### 9. Export IMDF
- Génération des fichiers :
  - venue
  - building
  - level
  - unit
  - opening
- Compression en `.zip`
---

## Stack technique
### Backend (Rust)
Framework API : Axum ou Actix  
Sérialisation : serde  
Géométrie : geo  
GeoJSON : geojson  
UUID : uuid  
Archive : zip  
### Frontend
Option simple :  
HTML + Canvas  
Option avancée :  
WebGL / Canvas API  
ou Rust → WASM  
### Base de données
PostgreSQL  
JSONB pour stockage du modèle  
### Structure IMDF
manifest.json  
venue.geojson  
building.geojson  
level.geojson  
unit.geojson  
opening.geojson  
amenity.geojson

## Roadmap
Phase 0 - Etude & Réflexion  
- format DWG
- format IMDF
- format DXF
- GeoJSON

Phase 1 — MVP
Carte + géocodage  
Dessin du footprint    

Phase 2 — Plan overlay 
Upload PNG  
Transform (scale / rotate / translate)  

Phase 3 — Géométrie
Dessin murs  
Snap system  

Phase 4 — Reconstruction
Polygonisation  
Génération pièces  

Phase 5 — Métier
Catégorisation  
édition utilisateur  

Phase 6 — Export
Génération IMDF  
ZIP export  