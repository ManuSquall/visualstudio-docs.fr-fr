---
title: 'Procédure : Ajouter des nœuds à l’espace de travail à partir de l’Explorateur de schémas XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6d4afaab4b0e687d1343e810002ae4ad46c869b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043972"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procédure : Ajouter des nœuds à l’espace de travail à partir de l’Explorateur de schémas XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment ajouter des nœuds à la [espace de travail du Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md) à partir de l’Explorateur de schémas XML. Pour cela, vous pouvez faire glisser-déplacer des nœuds à partir de l'Explorateur de schémas XML dans une vue du concepteur XSD, ou utiliser le menu contextuel de l'Explorateur de schémas XML. Vous pouvez également ajouter les nœuds mis en surbrillance suite à une recherche effectuée par l'Explorateur de schémas XML. Pour plus d'informations, voir [Procédure : Ajouter des nœuds de résultat de recherche de jeu de schémas à l’espace de travail](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Seuls des nœuds globaux peuvent être ajoutés à la [espace de travail Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Pour ajouter des nœuds via le menu contextuel de l'Explorateur de schémas XML  
  
1. Suivez les étapes de [Comment : Créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. Cliquez avec le bouton droit sur le nœud `PurchaseOrderType` dans l'Explorateur XSD. Sélectionnez **afficher dans la vue du graphique**.  
  
     Le nœud `purchaseOrderType` apparaît sur l'aire de conception de la vue du graphique.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Pour faire glisser-déplacer un nœud sur une vue  
  
1. Cliquez avec le bouton droit sur le nœud `PurchaseOrderType` dans la vue du graphique. Sélectionnez **afficher dans l’Explorateur de schémas XML**.  
  
     Le nœud est mis en surbrillance dans l'Explorateur de schémas XML.  
  
2. Cliquez avec le bouton droit sur le `PurchaseOrderType` nœud dans l’Explorateur de schémas XML, puis sélectionnez **afficher toutes les références**.  
  
     Le nœud `purchaseOrder` est mis en surbrillance.  
  
3. Faites glisser le nœud `purchaseOrder` sur la vue du graphique.  
  
     Le nœud `purchaseOrder` et le nœud `PurchaseOrderType` apparaissent en regard l'un de l'autre sur l'aire de conception de la vue du graphique. Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Pour ajouter des nœuds à l'aide de la fonction de recherche de l'Explorateur de schémas  
  
1. Tapez « purchaseOrder » dans la zone de texte de recherche de la [Explorateur XML](../xml-tools/xml-schema-explorer.md) barre d’outils et cliquez sur le bouton de recherche.  
  
     ![Recherche de mot clé de l’Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Les résultats de la recherche sont mis en surbrillance dans l'Explorateur de schémas XML et sont marqués par des graduations dans la barre de défilement verticale.  
  
2. Ajouter les résultats de recherche à l’espace de travail en cliquant sur le **ajouter des nœuds en surbrillance à l’espace de travail** bouton dans le volet de synthèse des résultats.  
  
     ![Résultat de recherche de l’Explorateur de schéma XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Le `purchaseOrder` nœud et le `PurchaseOrderType` nœud apparaissent en regard de chacun des autres sur l’aire de conception de la [vue du graphique](../xml-tools/graph-view.md). Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)
