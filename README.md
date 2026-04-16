# 倉庫番 Sokoban — Projet NSI Terminale

> **Projet pédagogique · Session 2026 · DarkSATHI Li**  
> Lycée · Spécialité Numérique et Sciences Informatiques (NSI) · Terminale

---

## Présentation

Ce dépôt contient un projet complet autour du jeu **Sokoban** (倉庫番, « gardien d'entrepôt », inventé en 1982), développé en Python dans le cadre de la spécialité NSI Terminale.

Le projet est structuré comme un **atelier pédagogique interactif** (page HTML autonome avec éditeurs PyScript) couvrant l'ensemble des thèmes du programme officiel de Terminale NSI : récursivité, POO, structures de données, graphes, programmation dynamique, SQL et interface graphique avec la bibliothèque Arcade.

---

## Aperçu

![Sokoban NSI](sokoban.png)

---

## Compétences mobilisées (Programme Terminale NSI)

| Thème | Contenu |
|---|---|
| **Récursivité** | Terminaison, variant, preuve formelle, pile d'appels |
| **POO & Héritage** | Classes `Niveau`, `Joueur`, `Partie`, `NiveauChrono` · `super().__init__()` · encapsulation · polymorphisme |
| **Structures de données** | Pile LIFO (`Historique`, annulation Ctrl+Z) · File FIFO (BFS) |
| **Graphes** | BFS parcours en largeur · DFS parcours en profondeur · composantes connexes · complexité O(V+E) |
| **Programmation dynamique** | Mémoïsation (top-down) · Tabulation (bottom-up) · Rendu de monnaie |
| **SQL** | `JOIN`, `GROUP BY`, `ORDER BY`, `HAVING`, `LIMIT` · base de données des scores |
| **Interface graphique** | Bibliothèque `arcade` · `SokobanWindow(arcade.Window)` · conversion de repères · palette RGB |

---

## Structure du projet

```
sokoban/
├── projet_sokoban.html   # Atelier interactif complet (PyScript 2026.3.1)
├── style.css             # Thèmes : sombre / clair / projecteur
├── sokoban.png           # Illustration du projet
└── README.md
```

---

## Contenu de l'atelier

L'atelier est organisé en **6 parties** accessibles depuis la barre de navigation :

### Partie 1 — Présentation
- Règles du jeu et tableau des symboles (`#`, `$`, `*`, `@`, `.`, `+`)
- Mini-jeu jouable directement dans le navigateur (Canvas JS, touches ↑↓←→ / ZQSD)
- Carte des compétences NSI mobilisées

### Partie 2 — Classes Python (POO)
- **Ex. 2.1** — `Niveau.afficher()` · dictionnaire de symboles emoji *(Débutant)*
- **Ex. 2.2** — `Joueur.deplacer(direction, niveau)` · vecteurs de déplacement, mise à jour de la grille *(Intermédiaire)*
- **Ex. 2.3** — `Partie.est_gagne()` · détection de victoire *(Débutant)*
- **Ex. 2.4** — `NiveauChrono(Niveau)` · héritage et `super().__init__()` *(Intermédiaire)*
- **Ex. 2.5** — `nb_caisses_placees(grille, idx)` · récursivité, variant `len(grille) - idx`, preuve de terminaison *(Intermédiaire)*
- **Ex. 2.6** — Classe `Historique` · pile LIFO, `empiler` / `depiler`, annulation de coups *(Avancé)*

### Partie 3 — SQL & Base de données
- Modèle relationnel : tables `joueurs`, `niveaux`, `parties`
- Requêtes : `SELECT`, `JOIN`, `WHERE`, `GROUP BY`, `ORDER BY`, `HAVING`, `LIMIT`
- Exercices progressifs sur les scores et classements

### Partie 4 — Graphes & Algorithmique
- **Ex. 4.1** — `voisins(grille, l, c)` · liste d'adjacence *(Débutant)*
- **Ex. 4.2** — `bfs_accessible(grille, depart, cible)` · BFS avec `collections.deque`, O(V+E) *(Intermédiaire)*
- **Ex. 4.3** — `dfs_composantes(grille)` · DFS, composantes connexes *(Avancé)*
- **Ex. 4.4** — Rendu de monnaie · mémoïsation ET tabulation *(Intermédiaire)*
- Tables d'états du BFS à compléter (exercice type épreuve écrite)

### Partie 5 — Interface graphique (Arcade)
- **Ex. 5.1** — `coords_arcade(ligne, col, taille, nb_lignes)` · conversion de repères (axe Y inversé) *(Débutant)*
- **Ex. 5.2** — Définition de la `PALETTE` RGB des 7 symboles *(Débutant)*
- **Ex. 5.3** — Dessin du plateau avec `arcade.draw_rect_filled` *(Intermédiaire)*
- **Ex. 5.4** — `SokobanWindow(arcade.Window)` · boucle de jeu complète avec HUD, BDD et historique *(Avancé)*

### Partie 6 — Préparation au baccalauréat
- Sujets type **Épreuve Pratique (EP2)** : `lire_csv`, `NiveauChrono`, `Historique`
- Questions type **Épreuve Écrite (Partie 1)** : piles/files, SQL, variant récursif, BFS vs DFS, complexité, mémoïsation
- Exercice de trace d'exécution récursive avec tableau pile d'appels à compléter

---

## Prérequis & lancement

### Consultation en ligne (sans installation)

Ouvrir `projet_sokoban.html` dans un navigateur moderne (Chrome, Firefox, Edge).  
PyScript 2026.3.1 (Pyodide/WASM) est chargé automatiquement depuis le CDN — **aucune installation requise**.

> ⚠️ La première ouverture peut prendre quelques secondes (chargement de Pyodide ~10 Mo).

### Utilisation locale de la bibliothèque Arcade (Partie 5)

Pour exécuter le code Arcade en dehors du navigateur :

```bash
pip install arcade
python sokoban_arcade.py
```

**Contrôles :**

| Touche | Action |
|---|---|
| ↑ ↓ ← → ou Z Q S D | Déplacer le joueur |
| Ctrl + Z | Annuler le dernier coup |
| R | Recommencer le niveau |
| Échap | Quitter |

---

## Technologies utilisées

- **Python 3.12+**
- **[PyScript 2026.3.1](https://pyscript.net/)** — Python dans le navigateur (Pyodide/WASM)
- **[Python Arcade 3.x](https://api.arcade.academy/)** — interface graphique desktop
- **SQLite 3** — base de données des scores
- **Bootstrap 5.3** — mise en page de l'atelier
- **MathJax 3** — notation mathématique (complexité O())
- **HTML5 Canvas** — mini-jeu intégré en JavaScript pur

---

## Thèmes d'interface

L'atelier propose trois thèmes accessibles depuis la barre de navigation :

| Thème | Usage recommandé |
|---|---|
| **Sombre** (défaut) | Travail personnel |
| **Clair** | Impression / accessibilité |
| **Projecteur** | Présentation en classe, vidéoprojecteur |

---

## Licence

Projet réalisé dans un cadre scolaire (NSI Terminale, session 2026).  
Usage pédagogique libre avec attribution.

---

*Lycée · Spécialité NSI Terminale · Session 2026*
