# Annuaire des acteurs du système alimentaire — structure Grist

Ce dépôt partage la **structure** (sans les données) de l'annuaire Grist « Annuaire des acteurs du système alimentaire ». Cet annuaire recense des projets liés aux transitions agricoles et alimentaires, ainsi que les structures et personnes qui y sont impliquées.

Il permet à d'autres territoires ou collectifs de reprendre le même modèle, et à toute personne intéressée de contribuer à l'outil.

## Contenu

| Dossier | Contenu |
|---|---|
| `grist/` | Le modèle Grist vide (`.grist`) à importer directement dans Grist |
| `schema/` | La description des tables, des colonnes et de leurs liens (`SCHEMA.md`, `schema.json`) |
| `referentiels/` | Les listes de valeurs partagées : étapes, sous-étapes, objectifs, types d'acteurs, labels |
| `modeles_import/` | Des CSV vides (en-têtes seulement) pour préparer des imports par lot |
| `widget/` | Le widget « réseau porteurs / partenaires » à coller dans le Widget Creator de Grist |
| `docs/` | Le guide de saisie et d'enrichissement de l'annuaire |

## Démarrer avec le modèle

1. Télécharge le fichier `grist/annuaire_acteurs_modele.grist`.
2. Sur [getgrist.com](https://www.getgrist.com/), clique sur **Ajouter** → **Importer un document** et choisis le fichier.
3. Importe les référentiels (`referentiels/*.csv`) s'ils ne sont pas déjà présents dans le modèle.
4. Saisis tes données, ou importe-les à partir des modèles CSV. L'ordre d'import est important : **Structures → Personnes_ressource → Acteurs**.

## Installer le graphe réseau

1. Ajoute un widget **Widget Creator** à une page, avec la table **Acteurs** comme source de données.
2. Colle le contenu de `widget/reseau_partenaires.html`, puis enregistre.
3. Dans le panneau de droite, onglet **Widget**, règle le niveau d'accès sur **Accès complet au document**. Le widget ne fait que lire les données.
4. Si tes tables ou colonnes portent d'autres noms, adapte le bloc `CFG` au début du code.

Le widget affiche les projets et les structures. Les porteurs sont reliés par un trait plein, les partenaires par un pointillé. Il propose des filtres par étape et par objectif, une recherche qui isole le réseau d'un acteur, et un encart de contact pour les personnes qui veulent contribuer.

## Contribuer

Collecte de données, recensement d'initiatives, évolution de l'outil… Pour rejoindre la démarche, écris à **arnaud.milet@d-sidd.com**.

Tu peux aussi ouvrir une *issue* sur ce dépôt pour proposer une évolution de la structure ou du widget.

## Conventions de saisie (résumé)

- Les **référentiels** (étapes, objectifs, types d'acteurs, labels) s'utilisent tels quels. Si une valeur manque, propose-la plutôt que de la créer.
- Une structure n'apparaît qu'**une fois** dans une liste. Elle est soit **porteuse** (elle pilote ou met en œuvre le projet), soit **partenaire** (financeur, soutien ou partenaire), jamais les deux pour un même projet.
- Le **SIRET** compte 14 chiffres, sans espace. On ne le saisit que s'il a été vérifié sur [annuaire-entreprises.data.gouv.fr](https://annuaire-entreprises.data.gouv.fr/).
- On ne saisit **pas de donnée personnelle non publiée**. Une adresse e-mail n'est reportée que si elle est publiée telle quelle.

Les règles complètes sont dans [`docs/guide_enrichissement.md`](docs/guide_enrichissement.md).
