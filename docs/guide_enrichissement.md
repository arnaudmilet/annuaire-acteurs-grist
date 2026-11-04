# Guide d'enrichissement de l'annuaire

Ce guide décrit comment ajouter des projets, des structures et des personnes à l'annuaire sans créer de doublons ni d'informations non vérifiées.

## 1. Inventaire

1. Parcourir la source : un site, une rubrique et ses sous-pages, un rapport…
2. Lister tous les projets, avec leur nom et leur URL.
3. Pour chacun, indiquer s'il est **nouveau** ou **déjà présent** dans `Acteurs`, en comparant à la fois l'URL et le nom.

## 2. Extraction

Pour chaque projet nouveau, remplir les champs de `Acteurs` (voir `schema/SCHEMA.md`) :

- **Description** : 2 à 5 phrases **reformulées**, sans copier le texte de la source.
- **Étape / Objectif** : uniquement des valeurs du référentiel.
- **Territoire** : au format « Commune (Département) », ou le niveau le plus précis disponible.

## 3. Rapprochement

Avant de créer une structure ou une personne, la chercher dans la base :

- Ignorer la casse, les accents, les espaces et les variantes de forme : « Ville de Montpellier » = « Commune de Montpellier », sigle = nom développé.
- Si elle existe, réutiliser son libellé **à l'identique**.
- En cas de doute, la créer comme nouvelle et signaler le rapprochement possible.

## 4. Règles

| Sujet | Règle |
|---|---|
| Pas d'invention | Un champ que ne documentent ni la source, ni une page du même site, ni une source officielle reste **vide**. |
| Doublons | Un même libellé n'apparaît qu'une fois dans une liste. |
| Porteur ou partenaire | Le porteur pilote ou met en œuvre le projet. Financeurs, soutiens et partenaires vont dans `Partenaires_impliques`. Une structure ne figure jamais dans les deux champs d'un même projet. |
| Est_un_projet_en_soi | Vrai si la structure est elle-même un projet de `Acteurs`. |
| Structure mère | Seulement si le lien est explicite : antenne locale d'un réseau national, service d'une collectivité… |
| SIRET | 14 chiffres sans espace, uniquement s'il est vérifié sans ambiguïté sur annuaire-entreprises.data.gouv.fr (de préférence le SIRET du siège). |
| Personnes | Seulement les personnes nommées publiquement comme contact ou coordination. Une adresse e-mail n'est reportée que si elle est publiée telle quelle ; on ne la déduit jamais. |
| Projets déjà présents | Pas de nouvelle ligne : proposer les compléments (valeur actuelle → valeur proposée). |
| Référentiels | Ne pas créer de nouvelle valeur. Proposer les ajouts (sous-étapes, objectifs, types) dans un rapport ou une *issue*. |

## 5. Livrables d'un lot d'import

1. Trois CSV contenant **uniquement des ajouts**, à importer dans cet ordre : `Structures` → `Personnes_ressource` → `Acteurs`.
   - Encodage UTF-8 avec BOM, séparateur point-virgule.
   - Dans les listes de références, les libellés exacts sont séparés par des virgules et la cellule est entre guillemets ; jamais d'identifiants, ni de colonne `id`.
2. Un rapport de contrôle contenant les rapprochements effectués ou douteux, les classements incertains, les compléments proposés pour les projets existants, les manques du référentiel et les pages inaccessibles.

Les modèles CSV vides sont dans `modeles_import/`.
