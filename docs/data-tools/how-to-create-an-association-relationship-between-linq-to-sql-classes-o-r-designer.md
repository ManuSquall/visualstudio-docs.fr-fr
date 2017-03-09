---
title: "Proc&#233;dure&#160;: cr&#233;er une association (relation) entre des classes LINQ to SQL (Concepteur O/R) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Proc&#233;dure&#160;: cr&#233;er une association (relation) entre des classes LINQ to SQL (Concepteur O/R)
Les associations entre classes d'entité dans [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sont analogues aux relations entre les tables dans une base de données.Vous pouvez créer des associations entre des classes d'entité en utilisant la boîte de dialogue **Éditeur d'associations**.  
  
 Vous devez sélectionner une classe parente et une classe enfant lorsque vous utilisez la boîte de dialogue **Éditeur d'associations** pour créer une association.La classe parente est la classe d'entité qui contient la clé primaire ; la classe enfant est la classe d'entité qui contient la clé étrangère.Par exemple, si les classes d'entité ont été créées pour mapper aux tables Customers et Orders de Northwind, la classe Customer constitue la classe parente et la classe Order, la classe enfant.  
  
> [!NOTE]
>  Lorsque vous faites glisser des tables de l'**Explorateur de serveurs**\/**Explorateur de bases de données** vers le [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), les associations sont créées automatiquement selon les relations de clé étrangère qui existent dans la base de données.  
  
 Après avoir créé une association, lorsque vous sélectionnez l'association dans le Concepteur O\/R, la fenêtre **Propriétés** contient des propriétés configurables.\(L'association est la ligne entre les classes connexes.\) Le tableau suivant décrit les propriétés d'une association.  
  
|Propriété|Description|  
|---------------|-----------------|  
|**Cardinalité**|Détermine s'il s'agit d'une l'association est un\-à\-plusieurs ou un\-à\-un.|  
|**Propriété enfant**|Spécifie s'il faut créer, dans le parent, une propriété qui est une collection ou une référence aux enregistrements enfants sur le côté clé étrangère de l'association.Par exemple, dans l'association entre Customer et Order, si la propriété **Child** a la valeur **True**, une propriété nommée Orders est créée dans la classe parente.|  
|**Propriété parent**|Propriété de la classe enfant qui fait référence à la classe parente associée.Par exemple, dans l'association entre Customer et Order, une propriété nommée Customer qui fait référence au client associé à une commande est créée dans la classe Order.|  
|**Propriétés participantes**|Affiche les propriétés d'associations et fournit un bouton de **sélection** \(…\) qui ouvre la boîte de dialogue **Éditeur d'associations**.|  
|**Unique**|Spécifie si les colonnes cibles étrangères ont une contrainte d'unicité.|  
  
### Pour créer une association entre des classes d'entité  
  
1.  Cliquez avec le bouton droit sur la classe d'entité qui représente la classe parente dans l'association, pointez sur **Ajouter**, puis cliquez sur **Association**.  
  
2.  Vérifiez que la **Classe parente** correcte est sélectionnée dans la boîte de dialogue **Éditeur d'associations**.  
  
3.  Sélectionnez la **Classe enfant** dans la zone de liste déroulante.  
  
4.  Sélectionnez les **Propriétés d'association** qui lient les classes.En général, un mappage à la relation de clé étrangère définie dans la base de données est alors établi.Par exemple, dans les associations Customers et Orders, les **Propriétés d'association** sont les CustomerID pour chaque classe.  
  
5.  Cliquez sur **OK** pour créer l'association.  
  
## Voir aussi  
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procédure pas à pas : création de classes LINQ to SQL \(Concepteur O\/R\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [Méthodes DataContext \(Concepteur O\/R\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure : représenter des clés primaires](../Topic/How%20to:%20Represent%20Primary%20Keys.md)