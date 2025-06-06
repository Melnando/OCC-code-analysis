# Minesweeper Solver - Analyse de Code Obfusqué avec SonarQube Cloud

## À propos

Ce projet est une **analyse statique d’un code en C obfusqué**, réalisé à l’aide de l’outil **SonarQube Cloud**. Le code choisi est un clone du jeu *Minesweeper*, issu du concours **IOCCC (International Obfuscated C Code Contest)**.

Le dépôt GitHub contient le code source tel qu’analysé, accompagné de ce rapport et de la configuration utilisée pour SonarCloud.

Code source original : [IOCCC 2020 Minesweeper](https://www.ioccc.org/years-spoiler.html)  

---

## Objectif du projet

- **Évaluer la qualité d’un code volontairement obfusqué**
- Utiliser **SonarQube Cloud** pour identifier :
  - Bugs critiques
  - Vulnérabilités
  - Code smells
  - Hotspots de sécurité
- Mettre en lumière les **défauts de lisibilité et de sécurité** du code C dans un contexte embarqué

---

## Méthodologie

1. Création du projet sur SonarCloud avec un lien direct au dépôt GitHub
2. Exécution de l’analyse statique via l’intégration GitHub → SonarCloud
3. Revue détaillée des résultats selon les catégories suivantes :
   - Complexité
   - Duplication
   - Couverture conditionnelle
   - Bugs
   - Code smells
   - Sécurité

---

## Résultats d’analyse (SonarCloud)

### Qualité de la branche principale : **Échec (Quality Gate)**

| Type                     | Nombre | Détails clés                                                                 |
|--------------------------|--------|------------------------------------------------------------------------------|
| 🐞 Bugs                  | 3      | Accès mémoire hors limites → risque de buffer overflow                      |
| 🔐 Vulnerabilités        | 0      | Aucune détectée                                                              |
| 👃 Code smells           | 44     | Noms non explicites, imbrication excessive, mauvaises pratiques             |
| 🔥 Security hotspots     | 1      | Utilisation risquée de `rand()` → cryptographie faible                      |
| 📉 Couverture            | N/A    | Non mesurée (code sans tests unitaires explicites)                          |

---

## 🧠 Problèmes détectés

### 🐛 Bugs critiques
- **Accès mémoire hors tableau** (array out-of-bounds)
- **Pré-déréférencement mémoire** avant le début d’un bloc

### 👃 Code smells notables
- **Complexité cognitive extrême** (plus de 7 niveaux imbriqués de `if/for`)
- **Noms de variables peu clairs** et absence de commentaires
- **Utilisation de chaînes dynamiques dans les formats printf**
- **Indentation et structures incohérentes**

### 🔥 Hotspot de sécurité
- **Utilisation de `rand()`** pour générer des nombres pseudo-aléatoires : à éviter pour des contextes de sécurité

---

## 📚 Enseignements

- L’analyse rappelle les bonnes pratiques vues dans les cours de **sécurité logicielle embarquée** :
  - Importance du **contrôle des accès mémoire**
  - Nécessité d’**éviter l’obfuscation excessive**
  - Utilité des outils d’**analyse statique pour repérer des failles critiques**

---

## 🧑‍💻 Auteurs

Projet réalisé dans le cadre du cours **"Securing Embedded Software"** en année 4 à l'ESILV

- **Melchior THIERRY** 
- **Aline WANG**
- 
📅 Date : 13/12/2023

