## Téléchargement
https://public.opendatasoft.com/explore/dataset/hydrographie-cours-deau/map/?flg=fr&refine.franchisst=Barrage&location=14,47.12347,-1.31094&basemap=jawg.light

# Documentation
https://geoservices.ign.fr/documentation/donnees/vecteur/bdtopo

# Description des données

## **Fictif** :
Tronçon hydrographique La valeur Fictif="Vrai" indique que la géométrie du Tronçon hydrographique n'est pas significative. L'axe fictif sert à doubler une Surface hydrographique afin d'assurer une continuité d'itinéraire linéaire pour les Cours d'eau.
cf

![[DC_BDTOPO_3-2.pdf#page=24]]]]

## Précision altimétrique
|Format PostgreSQL | Format Shapefile|
|-|-|
|precision_altimetrique | PREC_ALTI| 
| |Longueur maximale : 4|


**Type :** Décimal (5,1) 
**Classes concernées :** 
Bâtiment | Canalisation | Cimetière | Construction linéaire | Construction ponctuelle | Construction surfacique | Equipement de transport | Ligne électrique | Ligne orographique | Noeud hydrographique | Piste d'aérodrome | Point du réseau | Poste de transformation | Pylône | Réservoir | Surface hydrographique | Terrain de sport | Transport par câble | Tronçon de route | Tronçon de voie ferrée | Tronçon hydrographique 

**Définition :**
Précision altimétrique (en mètres) de la géométrie décrivant l'objet. 

**Contrainte sur l'attribut :**
Valeur obligatoire. La valeur "9999.0" correspond aux objets sans information altimétrique.