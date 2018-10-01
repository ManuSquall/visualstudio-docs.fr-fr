---
title: 'Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O-R) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14b60094150467aeda7641d018e06db15e7bda03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493729"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O-R)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer).  
  
  
Les associations entre classes d'entité dans [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sont analogues aux relations entre les tables dans une base de données. Vous pouvez créer des associations entre les classes d’entité à l’aide de la **Éditeur d’associations** boîte de dialogue.  
  
 Vous devez sélectionner une classe parente et la classe enfant lorsque vous utilisez le **Éditeur d’associations** boîte de dialogue pour créer une association. La classe parente est la classe d'entité qui contient la clé primaire ; la classe enfant est la classe d'entité qui contient la clé étrangère. Par exemple, si les classes d'entité ont été créées pour mapper aux tables Customers et Orders de Northwind, la classe Customer constitue la classe parente et la classe Order, la classe enfant.  
  
> [!NOTE]
>  Lorsque vous faites glisser les tables à partir de **Explorateur de serveurs**/**Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), les associations sont automatiquement créées en fonction existant relations de clé étrangère dans la base de données.  
  
 Après avoir créé une association, lorsque vous sélectionnez l’association dans le Concepteur O/R, il existe des propriétés configurables dans le **propriétés** fenêtre. (L'association est la ligne entre les classes connexes.) Le tableau suivant décrit les propriétés d'une association.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**cardinalité**|Détermine s'il s'agit d'une l'association est un-à-plusieurs ou un-à-un.|  
|**Propriété enfant**|Spécifie s’il faut créer, dans le parent, une propriété qui est une collection ou une référence aux enregistrements enfants sur le côté clé étrangère de l’association. Par exemple, dans l’association entre Customer et Order, si le **propriété enfant** a la valeur **True**, une propriété nommée Orders est créée dans la classe parente.|  
|**Propriété parent**|Propriété de la classe enfant qui fait référence à la classe parente associée. Par exemple, dans l'association entre Customer et Order, une propriété nommée Customer qui fait référence au client associé à une commande est créée dans la classe Order.|  
|**Propriétés participantes**|Affiche les propriétés d’associations et fournit un **points de suspension** bouton (...) qui ouvre le **Éditeur d’associations** boîte de dialogue.|  
|**unique**|Spécifie si les colonnes cibles étrangères ont une contrainte d'unicité.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>Pour créer une association entre des classes d'entité  
  
1.  Avec le bouton droit de la classe d’entité qui représente la classe parente dans l’association, pointez sur **ajouter**, puis cliquez sur **Association**.  
  
2.  Vérifiez que le bon **classe parente** est sélectionné dans le **Éditeur d’associations** boîte de dialogue.  
  
3.  Sélectionnez le **classe enfant** dans la zone de liste déroulante.  
  
4.  Sélectionnez le **propriétés d’Association** qui lient les classes. En général, un mappage à la relation de clé étrangère définie dans la base de données est alors établi. Par exemple, dans l’association Customers et Orders, la **propriétés d’Association** sont les CustomerID pour chaque classe.  
  
5.  Cliquez sur **OK** pour créer l’association.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Guide pratique pour représenter les clés primaires](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

