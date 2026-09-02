# 📙 Jour 3 — Tri et filtres

<p>
  <img src="https://img.shields.io/badge/Sprint%201-Fondamentaux-12294A" alt="Sprint 1">
  <img src="https://img.shields.io/badge/Jour-03%20%2F%2030-FF7900" alt="Jour 03">
  <img src="https://img.shields.io/badge/Statut-Termin%C3%A9-2E7D32" alt="Terminé">
  <img src="https://img.shields.io/badge/Livrables-5%20exercices%20%2B%20mini--projet%20%2B%20challenge-blue" alt="Livrables">
</p>

> **En une phrase :** trier réorganise les données, filtrer sélectionne celles qui répondent à un critère — et la combinaison des deux constitue déjà une analyse.

[⬅️ Retour au Sprint 1](../README.md) · [🏠 Sommaire du bootcamp](../../README.md)

---

## 📎 Livrables

| Fichier | Description |
|:---|:---|
| [📕 Rapport complet (PDF)](./documentation/Jour3_Excel_Tri_Filtres_Ndeye_Penda_SARR.pdf) | Version illustrée et détaillée, lisible directement dans GitHub |
| [📝 Rapport complet (Word)](./documentation/Jour3_Excel_Tri_Filtres_Ndeye_Penda_SARR.docx) | Version éditable du rapport |
| [📊 Classeur Excel](./exercices/Classeur-J03.xlsx) | Les 5 exercices, le mini-projet et le challenge |
| [📸 Captures](./captures/) | 43 preuves visuelles des manipulations |

---

## 🎯 Objectifs de la journée

- Trier des données selon une ou plusieurs colonnes, en préservant l'intégrité des lignes
- Filtrer selon un critère, puis selon plusieurs critères simultanés
- Utiliser les filtres numériques personnalisés (supérieur à, inférieur à, entre)
- Construire un tri hiérarchique à plusieurs niveaux
- Exploiter tri et filtres pour produire une première analyse sur une base de 1 000 étudiants

---

## 🧩 La notion clé de la journée

| | Trier | Filtrer |
|:---|:---|:---|
| **Effet** | Réorganise l'ordre des lignes | Masque les lignes hors critère |
| **Données** | Toutes restent visibles | Toutes sont conservées, certaines cachées |
| **Réversible** | L'ordre précédent est perdu | Oui, en retirant le filtre |
| **Sert à** | Classer, hiérarchiser | Sélectionner une population |

⚠️ **Le piège le plus dangereux de la journée :** trier une seule colonne sans les autres. Excel n'affiche aucune erreur, mais la note d'un étudiant se retrouve associée au nom d'un autre. Le tableau reste lisible — il a simplement cessé de dire la vérité.

---

## 🧪 Exercices réalisés

<details>
<summary><strong>Exercice 1 — Trier les données</strong></summary>

Point de départ : le tableau des étudiants, mis en forme selon les acquis du Jour 2.

![Tableau de données brutes](./captures/01-tableau-donnees-brutes.png)

**L'avertissement à ne jamais ignorer** — Excel demande s'il doit étendre la sélection à tout le tableau. La réponse est toujours **Étendre la sélection**.

![Avertissement étendre la sélection](./captures/03-avertissement-etendre-la-selection.png)

**➊ Tri par note de Math, du plus grand au plus petit**

![Dialogue de tri Math](./captures/04-dialogue-tri-math-decroissant.png)
![Résultat du tri Math](./captures/05-resultat-tri-math-decroissant.png)

**➋ Tri par nom, de A à Z**

![Dialogue de tri Nom](./captures/07-dialogue-tri-nom-a-z.png)
![Résultat du tri Nom](./captures/08-resultat-tri-nom-a-z.png)

**➌ Tri par date d'inscription, de la plus ancienne à la plus récente**

![Résultat du tri chronologique](./captures/10-resultat-tri-date-chronologique.png)

📅 Le format de la colonne a été vérifié avant le tri : une date reconnue comme du texte serait classée alphabétiquement, donc dans le désordre.
</details>

<details>
<summary><strong>Exercice 2 — Utiliser les filtres</strong></summary>

**➊ Filière = Data**

![Menu de filtre Filière](./captures/12-menu-filtre-filiere-data.png)
![Résultat filtre Data](./captures/13-resultat-filtre-filiere-data.png)

**➋ Présence supérieure à 90 %** — via Filtres numériques › Supérieur à

![Dialogue présence supérieure à 90](./captures/15-dialogue-presence-superieure-90.png)
![Résultat présence supérieure à 90](./captures/16-resultat-presence-superieure-90.png)

🔢 La valeur saisie dans le dialogue est `0,9`, alors que la cellule affiche `90 %`. Le filtre travaille sur la **valeur stockée**, jamais sur l'affichage — la notion du Jour 2 se vérifie ici concrètement.

**➌ Python inférieur à 10**

![Dialogue Python inférieur à 10](./captures/20-dialogue-python-inferieur-10.png)
![Résultat Python inférieur à 10](./captures/21-resultat-python-inferieur-10.png)
</details>

<details>
<summary><strong>Exercice 3 — Croiser plusieurs critères</strong></summary>

Plutôt que d'empiler des filtres temporaires, j'ai matérialisé chaque cas dans une **colonne de résultat** avec `SI` et `ET`. Le résultat reste visible pour tous les étudiants, et non seulement pour les lignes retenues.

**Cas 1 — Filière Data et présence élevée**

![Cas 1 formule SI ET](./captures/22-cas1-formule-si-et-filiere-presence.png)

**Cas 2 — Python ≥ 15 et Excel ≥ 15**

```excel
=SI(ET(G2>=15;H2>=15);"Validé";"Refusé")
```

![Cas 2 formule SI ET](./captures/23-cas2-formule-si-et-python-excel.png)

**Cas 3 — Ville = Dakar et Math < 10**

![Cas 3 formule SI ET](./captures/24-cas3-formule-si-et-ville-math.png)

💡 **Pourquoi une colonne plutôt qu'un filtre ?** Un filtre masque : le résultat disparaît dès qu'on le retire. Une colonne calculée conserve la trace de l'analyse pour chaque ligne et reste exploitable pour un tri, un comptage ou un tableau croisé.
</details>

<details>
<summary><strong>Exercice 4 — Filtres personnalisés</strong></summary>

**➊ Math entre 10 et 15** — deux conditions combinées avec ET dans le même dialogue

![Dialogue Math entre 10 et 15](./captures/25-dialogue-math-entre-10-et-15.png)
![Résultat Math entre 10 et 15](./captures/26-resultat-math-entre-10-et-15.png)

**➋ Présence entre 80 % et 90 %**

![Dialogue présence entre 80 et 90](./captures/27-dialogue-presence-entre-80-et-90.png)
![Résultat présence entre 80 et 90](./captures/28-resultat-presence-entre-80-et-90.png)

**➌ Frais payés supérieurs à 100 000 FCFA**

![Dialogue frais supérieurs à 100000](./captures/30-dialogue-frais-superieurs-100000.png)
![Résultat frais supérieurs à 100000](./captures/31-resultat-frais-superieurs-100000.png)

⌨️ La saisie se fait sans espace ni suffixe : `100000`. Le format d'affichage n'a pas à être reproduit dans le filtre.
</details>

<details>
<summary><strong>Exercice 5 — Trier selon plusieurs colonnes</strong></summary>

**➊ Filière (A → Z), puis Python (décroissant)**

![Dialogue tri Filière puis Python](./captures/32-dialogue-tri-filiere-puis-python.png)
![Résultat tri Filière puis Python](./captures/33-resultat-tri-filiere-puis-python.png)

**➋ Ville, puis Présence, puis Math**

![Dialogue tri à trois niveaux](./captures/34-dialogue-tri-ville-presence-math.png)
![Résultat tri à trois niveaux](./captures/35-resultat-tri-ville-presence-math.png)

🔍 **Observation importante :** les notes de Math n'apparaissent pas classées globalement. C'est normal — Math n'intervient qu'en troisième niveau, pour départager deux étudiants partageant déjà la même ville et la même présence.

Un tri multi-niveaux définit une hiérarchie explicite en une seule opération. Enchaîner plusieurs tris simples ferait perdre le résultat du précédent à chaque fois.
</details>

---

## 🎯 Mini-projet — Identifier les meilleurs étudiants

Base de travail : **1 000 étudiants**.

<details>
<summary><strong>Analyse 1 — Le top 10 en Python</strong></summary>

Filtres numériques › **10 premiers**

![Dialogue les 10 premiers](./captures/36-dialogue-filtre-10-premiers.png)
![Résultat top 10 Python](./captures/37-resultat-top-10-python.png)

⚠️ Le filtre « 10 premiers » peut renvoyer **plus de dix lignes** en cas d'ex æquo sur la dixième valeur. À connaître avant d'annoncer un chiffre dans un rapport.
</details>

<details>
<summary><strong>Analyse 2 — Les étudiants réguliers</strong></summary>

Trois conditions simultanées : présence ≥ 90 %, Math ≥ 15 et Python ≥ 15.

```excel
=SI(ET(K2>=90%;F2>=15;H2>=15);"Satisfait";"Non satisfait")
```

![Colonne Résultats 1](./captures/42-formule-si-et-etudiants-reguliers.png)

✅ L'écriture `90 %` dans la formule est correcte : Excel l'interprète comme `0,9`.
</details>

<details>
<summary><strong>Analyse 3 — Les étudiants à accompagner</strong></summary>

Moins de 10 en Math **ou** moins de 10 en Python.

```excel
=SI(OU(F2<10;H2<10);"Redouble";"Passe")
```

![Colonne Résultats 2](./captures/43-formule-si-ou-etudiants-a-accompagner.png)

🔑 **C'est ici qu'apparaît la limite du filtre standard.** Excel combine toujours les filtres de colonnes avec **ET** : appliquer `Math < 10` puis `Python < 10` donnerait les étudiants faibles dans **les deux** matières, pas dans l'une **ou** l'autre. La colonne calculée est la façon la plus simple d'exprimer un OU entre deux colonnes.
</details>

<details>
<summary><strong>Analyse 4 — Le classement par filière</strong></summary>

Filtrer une filière, trier Python en décroissant, lire les trois premières lignes, répéter.

![Dialogue tri Python par filière](./captures/38-dialogue-tri-python-par-filiere.png)
![Top 3 par filière](./captures/39-resultat-top-3-par-filiere.png)

Le filtre définit le périmètre, le tri produit le classement à l'intérieur de ce périmètre.
</details>

---

## 🏆 Challenge — Les 20 meilleures performances globales

Contrainte : **sans utiliser de formule**.

Le tableau comportait déjà une colonne `Statistiques` représentant une performance globale. Un simple tri décroissant sur cette colonne suffit : les vingt premières lignes sont la réponse.

---

## ⚡ Mémo des raccourcis et fonctions

| Raccourci / fonction | Action |
|:---|:---|
| `Ctrl + Maj + L` | Activer ou désactiver les filtres |
| `Alt + Bas` sur un en-tête | Ouvrir le menu de filtre |
| `Données › Trier` | Ouvrir le tri multi-niveaux |
| `Ctrl + Maj + Bas` | Sélectionner jusqu'à la dernière ligne (vérifier l'étendue) |
| `=SI(condition;"A";"B")` | Renvoyer une valeur selon un test |
| `=ET(c1;c2;c3)` | Vrai si toutes les conditions sont vraies |
| `=OU(c1;c2)` | Vrai si au moins une condition est vraie |
| `=SOUS.TOTAL(9;plage)` | Somme des seules lignes **visibles** d'un tableau filtré |

---

## 💡 Points de vigilance retenus

1. **Toujours préserver l'intégrité des lignes** — une colonne triée seule produit des données fausses, sans aucun message d'erreur.
2. **Un filtre ne supprime rien** — il masque, et les données réapparaissent dès qu'on le retire.
3. **Le tri multi-niveaux est hiérarchique** — le critère suivant n'intervient qu'à l'intérieur des groupes formés par le précédent.
4. **Valeur ≠ affichage** — `0,9` peut s'afficher `90 %` ; filtres et formules travaillent sur la valeur stockée.
5. **Les filtres de colonnes se combinent avec ET** — pour un OU, passer par une colonne calculée ou un filtre avancé.

---

## 📁 Contenu du dossier

```text
J03-Tri-et-filtres/
│
├── README.md                    ← ce fichier
│
├── documentation/
│   ├── Jour3_Excel_Tri_Filtres_Ndeye_Penda_SARR.docx
│   └── Jour3_Excel_Tri_Filtres_Ndeye_Penda_SARR.pdf
│
├── exercices/
│   └── Classeur-J03.xlsx
│
└── captures/
    ├── 01-tableau-donnees-brutes.png
    ├── ...
    └── 43-formule-si-ou-etudiants-a-accompagner.png
```

---

## ✅ Statut

**Jour 3 terminé et validé.**
Compétence principale acquise : *explorer et analyser un jeu de données par le tri et le filtrage, en préservant l'intégrité du tableau et en sachant traduire des critères croisés en colonnes de résultat.*

---

<sub>Ndeye Penda SARR — Apprenante Promotion 8, Développement Data · Orange Digital Center · 2026</sub>
