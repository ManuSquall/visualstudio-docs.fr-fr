---
title: 'Procédure : Ajouter des nœuds de résultat de recherche de jeu de schémas à l’espace de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4fc312d4120ef8d1d0f2deb5acd3ce581e878570
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447114"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procédure : Ajouter des nœuds de résultat d’une recherche dans un jeu de schémas à l’espace de travail
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique explique comment ajouter des nœuds mis en surbrillance dans l'Explorateur de schémas XML suite à une recherche par mot clé dans l'espace de travail.  
  
> [!NOTE]
> Seuls des nœuds globaux peuvent être ajoutés à la [espace de travail](../xml-tools/xml-schema-designer-workspace.md).  
  
 Cet exemple utilise l’exemple [schéma de bon de commande](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Pour ajouter des nœuds de résultat de jeu de schémas  
  
1. Suivez les étapes de [Comment : Créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. Tapez « purchaseOrder » dans la zone de texte de recherche de la [Explorateur XML](../xml-tools/xml-schema-explorer.md) barre d’outils et cliquez sur le bouton de recherche.  
  
     ![Recherche de mot clé de l’Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Les résultats de la recherche sont mis en surbrillance dans l'Explorateur de schémas XML et sont marqués par des graduations dans la barre de défilement verticale.  
  
3. Ajouter les résultats de recherche à l’espace de travail en cliquant sur le **ajouter des nœuds en surbrillance à l’espace de travail** bouton dans le volet de synthèse des résultats.  
  
     ![Résultat de recherche de l’Explorateur de schéma XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Le `purchaseOrder` nœud et le `PurchaseOrderType` nœud apparaissent en regard de chacun des autres sur l’aire de conception de la [vue du graphique](../xml-tools/graph-view.md). Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.
