---
title: Explorateur de schémas XML - rechercher le jeu de schémas
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfbc41b24dd0e58dd24e0af99afe458d27f8ade6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930855"
---
# <a name="search-the-schema-set"></a>Rechercher le jeu de schémas

Le **Explorateur de schémas XML** vous permet de rechercher le schéma défini comme suit :

-   Recherche par mot clé

-   Recherche spécifique au schéma

## <a name="keyword-search"></a>recherches par mot clé ;

 Vous effectuez des recherches par mot clé en entrant une sous-chaîne dans le **recherche le jeu de schémas** zone de texte de la **Explorateur de schémas XML** barre d’outils.

 ![Recherche par mot clé de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif)

 Le **Explorateur de schémas XML** recherche le schéma défini pour les attributs suivants :

-   Tout attribut `name` ou `ref` qui correspond au mot clé spécifié. Vous trouverez les éléments, attributs, types, etc., par nom.

-   Attributs `schemaLocation` d'instructions d'inclusion.

-   Attributs `namespace` d'instructions d'importation.

## <a name="schema-specific-search"></a>Recherche spécifique au schéma

 Le **Explorateur de schémas XML** inclut également des recherches prédéfinies que vous pouvez accéder à l’aide du menu contextuel (clic droit) de la **Explorateur de schémas XML**. Pour plus d’informations sur les menus contextuels disponibles, consultez [menus contextuels](../xml-tools/context-menus-xml-schema-explorer.md). Vous pouvez également effectuer une recherche spécifique au schéma à partir de la vue de départ ; Pour plus d’informations, consultez la section « Détails du jeu schéma » dans le [vue de départ](../xml-tools/start-view.md) rubrique.

## <a name="display-and-navigate-search-results"></a>Afficher et naviguer parmi les résultats de recherche

 Une fois la recherche terminée, le volet de synthèse des résultats est ajouté à la barre d'outils avec les résultats de la recherche. Les résultats de recherche sont également mises en surbrillance dans le **Explorateur de schémas XML** et marqués par des graduations sur la barre de défilement verticale. Vous pouvez naviguer les résultats de recherche en utilisant le **aller au résultat recherche suivant** et **aller au résultat recherche précédent** boutons dans le volet de synthèse des résultats de la **Explorateur de schémas XML**barre d’outils ; à l’aide des touches du clavier **F3** et **MAJ**+**F3**; ou en cliquant sur les graduations dans la barre de défilement.

 Vous pouvez ajouter les résultats de recherche à l’espace de travail en cliquant sur le **ajouter des nœuds en surbrillance à l’espace de travail** bouton dans le volet de synthèse des résultats.

 ![Résultat de la recherche de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Résultats d’effacer la recherche

 Pour effacer les résultats de recherche, cliquez sur le **x** bouton dans le volet de synthèse des résultats de la **Explorateur de schémas XML** barre d’outils de recherche.

## <a name="see-also"></a>Voir aussi

- [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)