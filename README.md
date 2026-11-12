# Scout Saut en longueur

Application d'observation et de projet de cycle pour le saut en longueur (1AC / 2AC / 3AC).
Un seul fichier HTML, sans serveur : `scout-saut-longueur.html`. Elle est séparée de l'application Scout Volley 3×3.

Prof : ADNANE CHAIBI (nom modifiable dans l'application).

## Utilisation

1. Ouvrir `scout-saut-longueur.html` dans un navigateur (téléphone ou ordinateur).
2. Créer une classe en écrivant le niveau au début du nom : `1AC-1`, `2AC-3`, `3AC-2`…
3. Ajouter les élèves : coller une liste « Nom ; M/F » (l'arabe est accepté).
4. Choisir le test : **Test d'observation (TO)** en séance 1, **Test bilan (TB)** en dernière séance.
5. Saisir les sauts, un élève à la fois, puis ouvrir l'écran d'analyse.

## Ce que l'on observe (2 essais par élève)

| # | Critère | Choix |
|---|---|---|
| 1 | Point de départ | Faux / Correct |
| 2 | Course d'élan | Sprint / Progressive |
| 3 | Planche d'appel | Avant / Sur / Mordu |
| 4 | Ouverture / fermeture | Oui / Non |
| 5 | Mesure | en mètres, avec la virgule (ex. 2,85) |

- Si la planche est **Mordu**, l'essai est nul : la mesure est désactivée et vidée automatiquement.
- Un second appui sur le même choix l'efface.
- On retient le meilleur des 2 essais.

### Problèmes calculés

| Code | Problème | Vu quand |
|---|---|---|
| PD | Point de départ faux | Point de départ = Faux |
| SP | Course d'élan en sprint | Course d'élan = Sprint |
| AV | Appel avant la planche | Planche = Avant |
| MO | Essai mordu | Planche = Mordu |
| OF | Absence d'ouverture-fermeture | Ouverture / fermeture = Non |

Pourcentage = sauts où le problème a été vu / sauts observés.
40 % et plus : **priorité** (rouge). 20 à 40 % : **à travailler** (orange). Fiabilité suffisante à partir de 10 sauts.

Le choix « Sprint = problème » se change avec la constante `SPRINT_IS_PROBLEM` dans le code.

## Les écrans d'analyse

- **Analyse** : priorités classées et tableau par classe, avec les performances des garçons et des filles.
- **Grilles** : grille d'observation en paysage, une classe par page, ou grille vierge à remplir au stylo.
- **Rapport** « Analyse et interprétation des résultats » : analyse, causes possibles (hypothèses), conclusion.
- **Projet** : projet de cycle et une fiche par séance (3 ateliers avec schémas). Export Word (.docx).
- **Banque** : 94 situations classées par séquence et par cause. Impression ou export CSV.

Le test d'observation est un **diagnostic, pas une note**. Le professeur coche les causes qu'il a observées en classe, et le projet est construit à partir de ces cases.

## Du diagnostic au projet de cycle

- Pas de séance théorique : séance 1 = TO, dernière séance = TB.
- Deux séquences de même taille : 8 séances (3 + 3), 10 séances (4 + 4, par défaut), 12 séances (5 + 5).
- Séquence 1 : course d'élan et appel. Séquence 2 : impulsion, suspension, réception.
- Chaque problème est relié à ses causes possibles :

| Problème | Causes possibles (la plus fréquente d'abord) | Séquence |
|---|---|---|
| PD | marq, pied, reg | 1 |
| SP | acc, reg, vit | 1 |
| AV | peur, marq, pied | 1 |
| MO | reg, marq, acc, peur | 1 |
| OF | susp, ram, rec, seg | 2 |

- Chaque cause cochée reçoit une séance dans sa séquence, la plus lourde (plus fort pourcentage) en premier.
- Une cause « priorité » reçoit une deuxième séance s'il reste de la place.
- Les places libres sont remplies avec la progression par défaut du niveau.
- Par défaut, chaque problème prend sa propre cause : deux problèmes ne se disputent pas la même séance.
- Chaque séance compte 3 ateliers (classes de 35 à 43 élèves, rotation).
- Le module dépend de la date du TO : semestre 1 (septembre → 23 janvier) = Module 1, semestre 2 (31 janvier → juillet) = Module 2. Il peut être changé à la main.

## Barème

Le barème OP 2009 (saut en longueur, /6, 20 lignes de 0,30 point) est utilisé **seulement au TB**.

## Données

- Tout est enregistré dans le navigateur (`localStorage`, clé `sl-scout-db-v1`).
- Sauvegarde et restauration par fichier JSON (à faire avant de changer d'appareil).
- Thème clair ou sombre : `sl-theme`.

## Anciennes données

Les anciens tests (12 codes E1…R2) restent lisibles : les performances sont conservées. Seuls « mordu » (A0) et « appel loin de la planche » (A1) sont convertis en choix de la planche. Les autres anciens codes ne sont pas repris.

## Pour développer

- Fonctions principales : `statsOf`, `diagnose`, `projData`, `hypotheses`, `chosen`, `buildPlan`, `pickSits`, `projetHTML`, `ficheHTML`, `rapportHTML`, `gridPaper`, `DOCX`.
- `CRIT`, `AXES`, `ORDER`, `AXT` : critères observés, problèmes, et lien problème → causes.
- `window.__SL` est exposé pour les tests.
- À tester après chaque modification : erreurs JavaScript, impression PDF (une grille par classe), Word converti avec LibreOffice, affichage à 390 px.
- Tests actuels : 33 pages de projet pour 10 séances (3 niveaux), Word identique dans LibreOffice (pas encore testé dans Microsoft Word).

## En attente

- Message vocal d'un autre professeur sur l'observation (non transcrit).
- Colonne « Dispositif » étroite : les 3 schémas sont petits.
- Idées : version course de vitesse (CV), vidéos des séances 2 à 9.
