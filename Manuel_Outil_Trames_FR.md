# OUTIL TRAMES
## Manuel utilisateur — Version 1.1

**Martial Rossignol**  
Algorithme original : Jean-Noël Lafargue  
Licence CC BY-NC-SA 4.0

---

## 1. Présentation

Outil Trames est une application web de tramage artistique par lignes dirigées. Elle convertit une image source en un réseau de hachures dont la densité et la direction reproduisent les valeurs tonales de l'original. Le résultat est exportable en SVG vectoriel multi-calques compatible Inkscape, ou en PNG pour un usage direct.

Conçu pour la sérigraphie, la gravure, la risographie et toute technique d'impression où le tramage par lignes est préférable aux trames de points classiques.

> **Mode d'utilisation** — Outil Trames est un fichier HTML autonome qui s'ouvre directement dans le navigateur (Chrome, Firefox, Edge). Aucune installation requise. Ouvrir en **plein écran** (F11 sur Windows/Linux, Cmd+Ctrl+F sur Mac) — l'interface est conçue pour occuper toute la largeur de l'écran et les quatre colonnes ne sont pleinement visibles qu'en plein écran.

### Choix de la langue

Les boutons **FR** et **EN** apparaissent en bas de la colonne gauche. Le choix est mémorisé automatiquement dans le navigateur. Le changement est instantané et n'affecte pas les paramètres en cours.

### Crédits et licence

Développé par **Martial Rossignol**. Algorithme de tramage par lignes basé sur les travaux de **Jean-Noël Lafargue**.

Distribué sous licence [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fr) : utilisation libre à condition de citer les auteurs, pas d'usage commercial sans autorisation, redistribution sous la même licence.

### Interface — quatre colonnes

| Colonne Gauche | Colonne Image |
|---|---|
| Ouvrir / info image | Recadrage interactif (popup) |
| Format de sortie (série, numéro, orientation) | Tonalité (luminosité, contraste, gamma) |
| Mise en page (marge, cadre, zone cible) | Niveaux (noir/blanc entrée) |
| Position H et V | Amplitude gris |
| Export SVG / PNG | Flou gaussien / Netteté |
| Couleur/Mono — Sélecteur de langue | |

| Colonne Centrale | Colonne Traitement |
|---|---|
| Aperçu interactif | Paramètres de tramage |
| Zoom molette (centré curseur) | Épaisseur du trait |
| Pan clic-glisser | Vibration des lignes |
| Indicateur de zoom | Export / import JSON paramètres |
| Barre de statut | Liste des calques générés |

---

## 2. Workflow recommandé

> **Avant de commencer — plein écran obligatoire** — Ouvrir le fichier dans le navigateur, passer en plein écran (F11 / Cmd+Ctrl+F). Le logiciel ne nécessite aucune connexion internet.

### Étape 1 — Chargement de l'image
- Cliquer ⊕ **Ouvrir image** ou glisser-déposer dans la zone centrale
- Formats acceptés : PNG, JPG, GIF, WEBP
- L'image originale s'affiche dans la colonne Image pour le recadrage

> **Conseil** — Utiliser de préférence une image en niveaux de gris ou à fort contraste.

### Étape 2 — Recadrage (optionnel)
- Cliquer **✂ Recadrer…** pour ouvrir la fenêtre popup plein écran
- Choisir un ratio : Libre, Original, 1:1, 3:2, 2:3, 4:3, 3:4, 16:9
- Tracer la sélection en diagonale — le ratio est respecté automatiquement
- Cliquer **✓ Appliquer** — l'aperçu se met à jour immédiatement
- **↺ Image complète** annule le recadrage

### Étape 3 — Prétraitement de l'image

Travailler dans cet ordre :
1. **Niveaux** — ajuster Noir et Blanc entrée pour étirer l'histogramme
2. **Gamma** — corriger les tons moyens (> 1 éclaircit les midtones)
3. **Amplitude gris** — positif étire la gamme, négatif la comprime
4. **Comp. hautes lum.** — récupère les nuances dans les zones surexposées
5. **Luminosité / Contraste** — ajustements globaux en dernier
6. **Flou** — flou gaussien léger (1–2) pour des transitions plus douces
7. **Netteté** — accentue les contours pour des lignes plus définies

> **Ordre critique** — Toujours appliquer les niveaux et le gamma AVANT la luminosité/contraste.

### Étape 4 — Format de sortie
- Sélectionner la série (A, B ou C), le numéro (0 à 6) et l'orientation
- Définir la marge blanche et l'épaisseur du cadre
- Zone cible : choisir si le dessin doit occuper une surface réduite
- Position H / V : placer le dessin dans la zone

### Étape 5 — Paramètres de tramage
- **Calques (1–12)** : nombre de directions de hachures superposées
- **Seuil mini / maxi** : plage de luminosité traitée
- **Écart mini / maxi** : espacement entre les lignes (zones sombres / claires)
- **Angle départ** : orientation des hachures du premier calque
- **Épaisseur trait** : 0.8 par défaut, adapté à la sérigraphie fine

> **Sérigraphie** — Épaisseur 0.8, écart mini 6, écart maxi 20, 1 ou 2 calques. Éviter les angles proches de 0° ou 90°.

### Étape 6 — Vibration des lignes (optionnel)
- **Vibration trait** (0–5 px) : amplitude de l'ondulation perpendiculaire. Les extrémités restent fixes.
- **Fréq. vibration** (0.5–8) : nombre de cycles sur la longueur d'une ligne

> **Subtilité** — Amplitude 0.5–1.0, fréquence 2 : effet quasi imperceptible à l'impression qui humanise le tramage.

### Étape 7 — Gestion des calques
- Cliquer l'œil pour masquer/afficher un calque
- Les calques masqués sont conservés dans le SVG exporté

### Étape 8 — Export
- **↓ Exporter SVG** : SVG multi-calques Inkscape, coordonnées en mm
- **↓ Exporter PNG** : capture de l'aperçu (résolution écran)
- **↓ Param / ↑ Param** : sauvegarder/charger les paramètres en JSON

---

## 3. Référence des paramètres

### Colonne Gauche — Format et mise en page

| Paramètre | Plage | Description |
|---|---|---|
| Série | A, B, C | Série ISO |
| Numéro | 0–6 | A0 (841×1189) à A6 (105×148 mm) |
| Orientation | Portrait / Paysage | |
| Marge blanche | 0–50 mm | Espace entre bord papier et dessin |
| Épais. cadre | 0–10 mm | Filet autour du dessin (0 = pas de cadre) |
| Zone cible | Pleine page, ½ largeur, ½ hauteur, format ISO | Surface dans laquelle le dessin s'inscrit |
| Position H / V | Gauche/Centre/Droite — Haut/Milieu/Bas | Placement dans la zone |

### Colonne Image — Prétraitement

| Paramètre | Plage | Description |
|---|---|---|
| Luminosité | –100 / +100 | Décalage additif global |
| Contraste | –100 / +100 | Amplification autour du gris moyen |
| Comp. hautes lum. | 0 / 100 | Compression non-linéaire des clairs |
| Gamma | 0.1 / 3.0 | Courbe de puissance (1.0 = neutre) |
| Noir entrée | 0 / 254 | Seuil bas des niveaux |
| Blanc entrée | 1 / 255 | Seuil haut des niveaux |
| Amplitude gris | –100 / +100 | Étire (+) ou comprime (–) la gamme |
| Flou | 0 / 10 | Sigma du flou gaussien |
| Netteté | 0 / 5 | Filtre laplacien d'accentuation |

### Colonne Traitement — Tramage

| Paramètre | Plage | Description |
|---|---|---|
| Calques | 1–12 | Nombre de directions de hachures |
| Seuil mini | 0.001–0.999 | Luminosité à partir de laquelle les lignes apparaissent |
| Seuil maxi | 0.001–0.999 | Luminosité au-delà de laquelle les lignes disparaissent |
| Écart mini | 2–100 px | Espacement dans les zones sombres |
| Écart maxi | 2–100 px | Espacement dans les zones claires |
| Angle départ | 0–180° | Direction du premier calque |
| Épaisseur trait | 0.1–8 | Épaisseur en pixels (défaut 0.8) |
| Vibration trait | 0–5 | Amplitude de l'ondulation perpendiculaire |
| Fréq. vibration | 0.5–8 | Cycles d'ondulation par ligne |

---

## 4. Conseils et astuces

- Convertir l'image en niveaux de gris avant chargement si possible
- Recadrer AVANT de régler les paramètres de tramage
- Commencer avec 2 calques, angle 45°, écarts égaux à 15
- Les sliders Vibration ne relancent pas le tramage — réponse instantanée
- Le format par défaut (série, numéro, orientation) est mémorisé automatiquement
- Les calques masqués sont exportés avec `display="none"` dans le SVG — récupérables dans Inkscape

---

## 5. Structure de l'export SVG

- Namespaces inkscape: et sodipodi: inclus
- `document-units="mm"` — Inkscape ouvre en millimètres
- Calque **Fond** : rectangle blanc
- Calques **Trame 1–N** : un groupe par direction avec l'angle en degrés
- Calque **Cadre** : filet modifiable séparément
- Coordonnées en mm à 4 décimales

---

*Outil Trames v1.1 — © Martial Rossignol — CC BY-NC-SA 4.0*
