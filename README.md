# Outil Trames

**Tramage par lignes dirigées — application web autonome**

Outil Trames convertit une image source en un réseau de hachures dont la densité et la direction reproduisent les valeurs tonales de l'original. Le résultat est exportable en SVG vectoriel multi-calques compatible Inkscape, ou en PNG.

Conçu pour la sérigraphie, la gravure, la risographie et toute technique d'impression où le tramage par lignes est préférable aux trames de points classiques.

---

## Utilisation

Aucune installation requise. Le logiciel fonctionne entièrement dans le navigateur.

1. Télécharger le fichier `outil_trames_v1.html`
2. L'ouvrir dans Chrome, Firefox ou Edge
3. **Passer en plein écran** (F11 sur Windows/Linux, Cmd+Ctrl+F sur Mac) — l'interface est conçue pour fonctionner en plein écran

➡️ [Ouvrir en ligne](https://votre-pseudo.github.io/outil-trames/outil_trames_v1.html) *(remplacer avec votre URL GitHub Pages)*

---

## Fonctionnalités

- Tramage par lignes dirigées sur 1 à 12 calques superposés
- Recadrage interactif de l'image source avec ratio verrouillable
- Prétraitement complet : niveaux, gamma, contraste, compression hautes lumières, amplitude des gris, flou gaussien, netteté
- Vibration des lignes (effet dessiné à la main)
- Export SVG multi-calques compatible Inkscape (coordonnées en mm)
- Export PNG
- Sauvegarde / chargement des paramètres en JSON
- Formats papier A, B, C — numéros 0 à 6, portrait et paysage
- Interface 4 colonnes : format, prétraitement, aperçu interactif, tramage

---

## Interface

| Colonne | Contenu |
|---------|---------|
| **Gauche** | Format de sortie, mise en page, export SVG/PNG |
| **Image** | Recadrage, tonalité, niveaux, flou/netteté |
| **Centrale** | Aperçu interactif (zoom, pan) |
| **Traitement** | Paramètres de tramage, vibration, calques générés |

---

## Workflow recommandé

1. Ouvrir l'image source
2. Recadrer si nécessaire
3. Ajuster le prétraitement (niveaux, gamma, contraste)
4. Choisir le format de sortie
5. Régler les paramètres de tramage (calques, seuils, écarts, angle)
6. Ajuster l'épaisseur du trait et la vibration
7. Exporter en SVG ou PNG

---

## Crédits

**Développement** : Martial Rossignol  
**Algorithme de tramage par lignes** : basé sur les travaux de [Jean-Noël Lafargue](http://lafargue.eu)

---

## Licence

[Creative Commons Attribution — Pas d'Utilisation Commerciale — Partage dans les Mêmes Conditions 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.fr)

Vous êtes libre de :
- **Partager** — copier et redistribuer le logiciel
- **Adapter** — modifier et transformer le logiciel

Sous les conditions suivantes :
- **Attribution** — citer Martial Rossignol et Jean-Noël Lafargue
- **Pas d'utilisation commerciale** — sans autorisation explicite
- **Partage dans les mêmes conditions** — vos modifications sous la même licence

---

*Outil Trames — © Martial Rossignol — CC BY-NC-SA 4.0*
