---
title: Recherche le jeu de schémas | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6328e3febf8d7279ad0a4bcac3ca4be54eb42c20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="searching-the-schema-set"></a>Recherche dans le jeu de schémas
L'Explorateur de schémas XML vous permet d'effectuer les recherches suivantes dans le jeu de schémas :  
  
-   Recherche par mot clé  
  
-   Recherche spécifique au schéma  
  
## <a name="keyword-search"></a>Recherches par mot clé  
 Effectuer des recherches par mot clé en entrant une sous-chaîne dans la **recherche le jeu de schémas** zone de texte de la barre d’outils de l’Explorateur de schémas XML.  
  
 ![Recherche de mot clé de l’Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 L'Explorateur de schémas XML recherche les éléments suivants dans le jeu de schémas :  
  
-   Tout attribut `name` ou `ref` qui correspond au mot clé spécifié. Vous pouvez ainsi rechercher des éléments, des attributs, des types, etc. par nom.  
  
-   Attributs `schemaLocation` d'instructions d'inclusion.  
  
-   Attributs `namespace` d'instructions d'importation.  
  
## <a name="schema-specific-search"></a>Recherche spécifique au schéma  
 Vous pouvez également accéder aux recherches prédéfinies de l'Explorateur de schémas XML via son menu contextuel. Pour plus d’informations sur les menus contextuels disponibles, consultez [contextuels](../xml-tools/context-menus-xml-schema-explorer.md). Vous pouvez également effectuer une recherche spécifique au schéma à partir de la vue de départ ; Pour plus d’informations, consultez la section « Détails du document de schéma » dans le [vue de départ](../xml-tools/start-view.md) rubrique.  
  
## <a name="displaying-and-navigating-search-results"></a>Affichage et navigation des résultats de la recherche  
 Une fois la recherche terminée, le volet de synthèse des résultats est ajouté à la barre d'outils avec les résultats de la recherche. Les résultats de la recherche sont aussi mis en surbrillance dans l'Explorateur de schémas XML et sont marqués par des graduations dans la barre de défilement verticale. Vous pouvez naviguer les résultats de recherche en utilisant la **aller au résultat suivant** et **aller au résultat recherche précédent** boutons dans le volet de synthèse des résultats de la barre d’outils de l’Explorateur de schémas XML, à l’aide des touches du clavier F3 et MAJ + F3 ; ou en cliquant sur les marques de graduation dans la barre de défilement.  
  
 Vous pouvez ajouter les résultats de recherche à l’espace de travail en cliquant sur le **ajouter des nœuds en surbrillance à l’espace de travail** bouton dans le volet de synthèse des résultats.  
  
 ![Résultat de recherche de l’Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Effacement des résultats de la recherche  
 Pour effacer les résultats de recherche, cliquez sur le **x** bouton dans le volet de synthèse des résultats de la barre d’outils de recherche de l’Explorateur de schémas XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)