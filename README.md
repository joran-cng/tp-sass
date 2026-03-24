
# Rapport de TP : Architecture Sass 7-1 & Tailwind

**Auteur :** CAUNEGRE Joran
**Projet :** Structuration avancée et intégration hybride.

----------

## 1. Structure du projet (`src/sass`)

L'arborescence suit le pattern 7-1. Chaque fichier partiel (`_*.scss`) contient un commentaire précisant sa responsabilité.

-   **`abstracts/`** : Variables globales, mixins et fonctions (ne génèrent pas de CSS seul).

-   **`vendors/`** : Librairies externes (ex: `_normalize.scss`, `_swiper.scss`).

-   **`base/`** : Reset et typographie par défaut du projet.

-   **`layout/`** : Structure globale (Header, Footer, Navigation).

-   **`components/`** : Composants modulaires (Boutons, Cartes, Formulaires).

-   **`pages/`** : Styles spécifiques à certaines vues (Home, About).

-   **`themes/`** : Gestion du mode sombre et variantes de couleurs.


----------

## 2. Fichier principal (`main.scss`)

Ce fichier centralise les imports. L'ordre est critique pour respecter la cascade CSS (des outils vers les composants).

----------

## 3. Analyse et Réflexion (Sass vs Tailwind)

### 3.1 Requêtes IA

-   **Initialisation :** _"Lister les dossiers 7-1 Sass et leur rôle."_

-   **Optimisation :** _"Comment optimiser Sass 7-1 avec Tailwind CSS ?"_


### 3.2 Justification de l'approche hybride

Pourquoi garder cette structure avec Tailwind ?

1.  **Encapsulation :** On évite de surcharger le HTML avec des dizaines de classes utilitaires pour les composants complexes.

2.  **Maintenance :** Les styles de bibliothèques tierces (`vendors/`) restent isolés.

3.  **Logique :** Sass permet une logique de programmation (boucles, mixins) plus poussée que les utilitaires standards.


**Exemple par dossier :**

-   **`abstracts`** : Utile pour les tokens de design (ex: courbes de bézier) réutilisables en CSS pur.

-   **`components`** : Prioritaire pour créer des classes comme `.btn-premium`, gérant des états complexes (SVG, dégradés animés) difficiles à maintenir en Tailwind seul.


### 3.3 Cas concret : Bouton Premium

Le style de ce bouton est défini dans **`src/sass/components/_button.scss`**.

-   **Pourquoi Sass ?** Gestion d'un dégradé spécifique et d'une animation complexe sur l'icône SVG au survol.

-   **Logique :** Utilisation du nesting (`&`) et de transitions sur les enfants (`.icon-svg`) pour une lecture plus fluide que les variantes arbitraires de Tailwind.