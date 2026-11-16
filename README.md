# Scout Saut en longueur

Application d'observation et de projet de cycle pour le saut en longueur (1AC / 2AC / 3AC).
Un seul fichier HTML, sans serveur : `scout-saut-longueur.html`.

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
| 1 | Course d'élan | Sprint / Progressive |
| 2 | Piétinement | Oui / Non |
| 3 | Planche d'appel | Avant / Sur / Mordu |
| 4 | Ouverture / fermeture | Oui / Non |
| 5 | Mesure | en mètres, avec la virgule (ex. 2,85) |

- Si la planche est **Mordu**, l'essai est nul : la mesure est désactivée et vidée automatiquement.
- Un second appui sur le même choix l'efface.
- On retient le meilleur des 2 essais.
- **Saisie par essai pour toute la classe** : on fait l'essai 1 pour tous les élèves, puis l'application passe à l'essai 2 (retour au premier élève). L'essai 2 reste verrouillé tant que l'essai 1 n'est pas terminé pour la classe.
- **Passer** : un élève absent ou qui aide le professeur passe à la fin de la saisie (les listes imprimées gardent l'ordre d'origine).

### Problèmes calculés

| Code | Problème | Vu quand |
|---|---|---|
| SP | Course d'élan en sprint | Course d'élan = Sprint |
| PI | Piétinement avant la planche | Piétinement = Oui |
| AV | Appel avant la planche | Planche = Avant |
| MO | Essai mordu | Planche = Mordu |
| OF | Absence d'ouverture-fermeture | Ouverture / fermeture = Non |

Pourcentage = sauts où le problème a été vu / sauts observés.
40 % et plus : **priorité** (rouge). 20 à 40 % : **à travailler** (orange). Fiabilité suffisante à partir de 10 sauts.

Le choix « Sprint = problème » se change avec la constante `SPRINT_IS_PROBLEM` dans le code.

## Nombre de séances et de séquences
Le professeur choisit 8, 10 ou 12 séances (T.O. en séance 1, T.B. en dernière séance). Les deux séquences sont de taille égale (3+3, 4+4, 5+5). Pour 12 séances seulement, le nombre de séquences est **décidé automatiquement par les problèmes de la classe** : si les causes retenues touchent à la fois l'élan-appel et la suspension-réception, le site propose **3 séquences (4 + 3 + 3)** : élan et appel / impulsion (le lien entre les deux) / suspension et réception ; sinon 2 séquences de 5. Le professeur peut toujours forcer 2 ou 3 séquences.

## Corrections du 16/11/2026 (après audit)
- **Niveau manuel** : dans « Modifier la classe », on peut choisir 1AC / 2AC / 3AC si le nom ne commence pas par le niveau.
- **Zone d'appel** (option par niveau, dans « Modifier la classe ») : les choix deviennent « Avant la zone / Dans la zone / Mordu » (saisie, grille, légende) ; dans le rapport, le projet et les fiches (PDF et Word) de ce niveau, « planche » devient « zone » ; la mesure part de l'empreinte du pied d'appel.
- **Comportement moteur jugé sur les 2 essais** : bon choix aux 2 essais = tous les points du critère, à un seul = la moitié, à aucun = 0 (notes arrondies au quart de point).
- **Élève sans mémoire** (ou pied / distance non notés au TB) : 0 point pour ces critères, avec ⚠ dans le tableau. La séance de détermination est obligatoire : un élève absent la rattrape à un autre moment.
- **Tous les essais mordus** : Habileté = 0 (et non plus « — »).
- **Sexe non renseigné** : ⚠ « sexe » dans le tableau (pas de note de performance).
- **Note /20** (grille OP 2009) : pratique (Habileté /6 + Comportement moteur) + connaissances conceptuelles /3 + comportementales /3 (1AC), /4 (2AC), /5 (3AC), saisies avec le bouton « 📝 » au test bilan. Le CSV contient toutes ces colonnes.
- **Cycle de 8 séances** : pied d'appel et distance d'élan dans la même séance (séance 2).
- **Pied d'appel** : 1 saut sur chaque pied (classes de 30 à 40 élèves). **Distances d'élan** : 10, 15, 20, 25 m.
- La distance d'élan est fixée pendant la séance d'élan : si l'élève en change au test bilan, il perd le point.
- **Élève dispensé** (absent justifié aux séances de détermination) : bouton dans « Mémoire du cycle ». Pied et distance ne sont pas comptés et leurs points vont aux 4 autres critères. Sans dispense, pas de mémoire = 0 pour ces deux critères.
- **Import du comportement (CSV)** : au test bilan, bouton « 📥 Importer les notes de comportement ». Format attendu : `Niveau;Classe;Nom;Note_Comportement;Bareme;…` (séparateur `;` ou `,`). Les noms sont reliés aux élèves de la classe (même nom, mots dans un autre ordre, petites différences d'écriture : hamza, ة/ه…). La note est ramenée sur le maximum du niveau (/3, /4, /5). Le site affiche les noms non trouvés et les élèves sans note. Si le fichier contient plusieurs classes, seules les lignes de la classe ouverte sont prises.

## Mémoire du cycle (pied d'appel et distance d'élan)

- **Séance 2 (fixe)** : déterminer le pied d'appel (5 sauts sur chaque pied). **Séance 3 (fixe)** : déterminer la distance d'élan (10, 15, 20 ou 25 m). Ces deux séances sont toujours en début de séquence 1 ; les autres séances sont réparties selon les problèmes observés.
- Le professeur inscrit, pour chaque élève, le pied et la distance dans **« Mémoire du cycle »** (bouton sous la liste des élèves).
- Au **test bilan**, on note aussi le pied d'appel et la distance d'élan réellement utilisés. Même valeur que la mémoire = points (essai retenu pour la performance).
- **Notation du test bilan** (grille d'évaluation OP 2009) : **Habileté motrice /6** = la performance (barème OP 2009) ; **Comportement moteur /8 (1AC), /7 (2AC), /6 (3AC)** = les critères observés : course d'élan progressive, pas de piétinement, appel sur la planche, ouverture / fermeture, même distance d'élan et même pied d'appel que la mémoire. Le professeur règle les points de chaque critère (pas de 0,5 ; le total doit faire le maximum du niveau). Les critères sont évalués sur l'essai retenu pour la performance. Le tableau des résultats affiche Habileté, Comportement moteur et Total.
- Le CSV du test bilan contient la mémoire, les valeurs utilisées, le Comportement moteur et le total.

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
| SP | acc, reg, vit | 1 |
| PI | marq, reg, peur, pied | 1 |
| AV | peur, marq, pied | 1 |
| MO | reg, marq, acc, peur | 1 |
| OF | susp, ram, rec, seg | 2 |

- Séances 2 et 3 : fixes (pied d'appel, distance d'élan). Les autres : chaque cause cochée reçoit une séance dans sa séquence, la plus lourde (plus fort pourcentage) en premier.
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
