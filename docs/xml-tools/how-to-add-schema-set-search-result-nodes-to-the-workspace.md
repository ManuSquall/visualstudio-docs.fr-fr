---
title: "Proc&#233;dure&#160;: ajouter des nœuds de r&#233;sultat d&#39;une recherche dans un jeu de sch&#233;mas &#224; l&#39;espace de travail | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: ajouter des nœuds de r&#233;sultat d&#39;une recherche dans un jeu de sch&#233;mas &#224; l&#39;espace de travail
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment ajouter des nœuds mis en surbrillance dans l'Explorateur de schémas XML suite à une recherche par mot clé dans l'espace de travail.  
  
> [!NOTE]
>  Seuls des nœuds globaux peuvent être ajoutés à l'[espace de travail](../xml-tools/xml-schema-designer-workspace.md).  
  
 Cet exemple utilise l'exemple [Schéma de bon de commande](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md).  
  
### Pour ajouter des nœuds de résultat de jeu de schémas  
  
1.  Suivez les étapes dans [Procédure : créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Tapez « purchaseOrder » dans la zone de texte de recherche de la barre d'outils de l'[Explorateur XML](../xml-tools/xml-schema-explorer.md), puis cliquez sur le bouton de recherche.  
  
     ![Recherche par mot clé de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Les résultats de la recherche sont mis en surbrillance dans l'Explorateur de schémas XML et sont marqués par des graduations dans la barre de défilement verticale.  
  
3.  Ajoutez les résultats de la recherche à l'espace de travail en cliquant sur le bouton **Ajouter les nœuds en surbrillance à l'espace de travail** dans le volet de synthèse des résultats.  
  
     ![Résultat de la recherche de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Le nœud `purchaseOrder` et le nœud `PurchaseOrderType` apparaissent en regard l'un de l'autre sur l'aire de conception de la [vue du graphique](../xml-tools/graph-view.md).Étant donné que les deux nœuds sont associés \(l'élément `purchaseOrder` est du type `PurchaseOrderType`\), une flèche est dessinée entre eux.