---
title: Recherche dans le jeu de schémas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656160"
---
# <a name="searching-the-schema-set"></a>Recherche dans le jeu de schémas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'Explorateur de schémas XML vous permet d'effectuer les recherches suivantes dans le jeu de schémas :

- Recherche par mot clé

- Recherche spécifique au schéma

## <a name="keyword-search"></a>Recherches par mot clé
 Pour effectuer des recherches par mot clé, entrez une sous-chaîne dans la zone de texte **Rechercher dans schémas** de la barre d’outils de l’Explorateur de schémas XML.

 ![Recherche par mot clé de l’Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 L'Explorateur de schémas XML recherche les éléments suivants dans le jeu de schémas :

- Tout attribut `name` ou `ref` qui correspond au mot clé spécifié. Vous pouvez ainsi rechercher des éléments, des attributs, des types, etc. par nom.

- Attributs `schemaLocation` d'instructions d'inclusion.

- Attributs `namespace` d'instructions d'importation.

## <a name="schema-specific-search"></a>Recherche spécifique au schéma
 Vous pouvez également accéder aux recherches prédéfinies de l'Explorateur de schémas XML via son menu contextuel. Pour plus d’informations sur les menus contextuels disponibles, consultez [menus contextuels](../xml-tools/context-menus-xml-schema-explorer.md). Vous pouvez également effectuer une recherche spécifique au schéma à partir de la vue de départ. Pour plus d’informations, consultez la section « Détails du jeu de schémas » dans la rubrique [vue de départ](../xml-tools/start-view.md) .

## <a name="displaying-and-navigating-search-results"></a>Affichage et navigation des résultats de la recherche
 Une fois la recherche terminée, le volet de synthèse des résultats est ajouté à la barre d'outils avec les résultats de la recherche. Les résultats de la recherche sont aussi mis en surbrillance dans l'Explorateur de schémas XML et sont marqués par des graduations dans la barre de défilement verticale. Vous pouvez parcourir les résultats de la recherche en utilisant les boutons **aller au résultat de la recherche suivant** et **aller au résultat de la recherche précédent** dans le volet des résultats Résumé de la barre d’outils de l’Explorateur de schémas XML. en utilisant les touches du clavier F3 et Maj + F3 ; ou en cliquant sur les graduations dans la barre de défilement.

 Vous pouvez ajouter les résultats de la recherche à l’espace de travail en cliquant sur le bouton **Ajouter les nœuds en surbrillance à l’espace de travail** dans le volet des résultats de résumé.

 ![Résultat de la recherche dans l’Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Effacement des résultats de la recherche
 Pour effacer les résultats de la recherche, cliquez sur le bouton **x** dans le volet de synthèse des résultats de la barre d’outils recherche de l’Explorateur de schémas XML.

## <a name="see-also"></a>Voir aussi
 [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)
