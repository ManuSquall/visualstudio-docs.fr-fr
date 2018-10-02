---
title: Explorateur de schémas XML | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6fe09ca80bd9a5f4d94942adcfd98c139acdc6c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496188"
---
# <a name="xml-schema-explorer"></a>Explorateur de schémas XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Explorateur de schémas XML](https://docs.microsoft.com/visualstudio/xml-tools/xml-schema-explorer).  
  
  
L'Explorateur de schémas XML est intégré à Microsoft Visual Studio et l'Éditeur XML pour vous permettre d'utiliser les schémas en langage XSD (XML Schema Definition). Lorsque vous ouvrez un fichier de schéma XML, le **jeu de schémas** nœud apparaît dans l’Explorateur de schémas XML. Tous les schémas inclus, importés ou redéfinis pour votre fichier cible, ainsi que tous les fichiers référencés via une instruction `include` ou `import`, s'affichent également dans l'Explorateur de schémas XML.  
  
 L'Explorateur de schémas XML vous permet d'effectuer les opérations suivantes :  
  
-   obtenir une vue d'ensemble rapide du jeu de schémas ;  
  
-   Parcourir et naviguer l'arborescence.  
  
-   Effectuer des recherches par mot clé et spécifiques au schéma. Pour plus d’informations, consultez [recherche le jeu de schémas](../xml-tools/searching-the-schema-set.md).  
  
-   Ajouter les résultats de la recherche à la vue du graphique ou du modèle de contenu.  
  
-   trier l’arborescence par ordre des documents, par type ou par nom ; Pour plus d’informations, consultez [, filtrage, regroupement et tri](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
-   ouvrir l'éditeur XML et accéder aux emplacements de code dans le fichier XSD ; Pour plus d’informations, consultez [intégration avec l’éditeur XML](../xml-tools/integration-with-xml-editor.md).  
  
-   générer un exemple de code XML pour les éléments globaux.  
  
 L'Explorateur de schémas XML fournit une vue hiérarchique du jeu de schémas à travers une arborescence. L'Explorateur de schémas XML fournit également des fonctionnalités de recherche, de filtrage, de navigation et de tri. Pour accéder à l'Explorateur de schémas XML, effectuez l'une des opérations suivantes :  
  
-   Si vous êtes sur le [vue de départ](../xml-tools/start-view.md), cliquez sur le **Explorateur de schémas XML** lien.  
  
-   Si vous êtes sur le [vue du graphique](../xml-tools/graph-view.md) ou [affichage du modèle de contenu](../xml-tools/content-model-view.md) et avoir des nœuds dans votre espace de travail, utilisez le menu contextuel pour sélectionner l’Explorateur de schémas XML.  
  
-   Vous pouvez également sélectionner le Explorerfrom de schéma XML le **vue** menu.  
  
-   Vous pouvez accéder à la Explorerfrom de schéma XML un fichier .vb qui a un littéral de XML Visual Basic associé à un fichier .xsd. Pour afficher le schéma défini dans l’Explorateur de schémas XML, avec le bouton droit cliquez sur un nœud XML dans un littéral XML ou une importation d’espace de noms XML et sélectionnez le **afficher dans l’Explorateur de schémas** commande. Pour plus d’informations, consultez [intégration de littéraux XML avec l’Explorateur de schémas XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>arborescence  
 L'Explorateur de schémas XML affiche les informations sur le jeu de schémas précompilés dans une arborescence. L'arborescence est organisée comme suit :  
  
-   Au niveau supérieur se trouve le nœud de jeu de schémas.  
  
-   Le deuxième niveau contient les espaces de noms.  
  
-   Le troisième niveau contient les fichiers.  
  
-   Le quatrième niveau contient les nœuds globaux. Ceci peut inclure les éléments, les groupes, les types complexes, les types simples, les attributs, les groupes d'attributs, et les instructions `include`, `import` et `redefine`.  
  
 Voici un exemple d’arborescence :  
  
 ![Explorateur de schémas XML](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Sélection et activation  
 Pour mettre en surbrillance et sélectionner un nœud, cliquez une fois dans l'Explorateur de schémas.  
  
 Pour activer un nœud, double-cliquez dessus ou appuyez sur **entrée** lorsque le nœud est sélectionné.  
  
-   L'activation d'un nœud ouvre le fichier dans lequel ce nœud est défini (si le fichier n'est pas déjà ouvert) et sélectionne le nœud dans le fichier.  
  
-   L'activation d'un nœud de fichier ouvre le fichier sélectionné (s'il n'est pas déjà ouvert) et met en surbrillance le nœud `<schema>`.  
  
-   L'activation d'un jeu de schémas ou d'un nœud d'espace de noms n'aboutit à rien.  
  
## <a name="draging-and-dropping-nodes"></a>Déplacement de nœuds par glisser-déplacer  
 Vous pouvez glisser et déposer des nœuds, des nœuds de fichier et des nœuds d’espace de noms par glisser-déposer dans une vue du concepteur XSD. Si la vue actuelle est la [vue de départ](../xml-tools/start-view.md), faire glisser un nœud à la vue s’ouvre le [vue du graphique](../xml-tools/graph-view.md). Si la vue actuelle est la [affichage du modèle de contenu](../xml-tools/content-model-view.md) ou de la vue du graphique, la vue ne change pas lorsque vous supprimez un nœud sur celle-ci.  
  
 Suppression des fichiers sur la vue ajoutera tous les nœuds globaux dans le fichier pour le [espace de travail du concepteur XSD](../xml-tools/xml-schema-designer-workspace.md). Le dépôt d’espaces de noms sur la vue ajoute tous les nœuds globaux dans l’espace de noms à l’espace de travail. L'espace de travail est partagé entre toutes les vues.  
  
 Vous ne pouvez pas faire glisser-déplacer des importations ou des nœuds locaux.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Recherche dans le jeu de schémas](../xml-tools/searching-the-schema-set.md)  
  
-   [Tri, filtrage et regroupement](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Menus contextuels](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Intégration de littéraux XML avec l’Explorateur de schémas XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour ajouter des nœuds à l’espace de travail à partir de l’Explorateur de schémas XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)







