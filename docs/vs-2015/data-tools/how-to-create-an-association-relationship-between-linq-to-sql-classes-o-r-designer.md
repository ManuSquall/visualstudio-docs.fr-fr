---
title: 'Comment : créer une association (relation) entre des classes LINQ to SQL (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609998"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Comment : créer une association (relation) entre des classes LINQ to SQL (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les associations entre classes d'entité dans [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sont analogues aux relations entre les tables dans une base de données. Vous pouvez créer des associations entre des classes d’entité en utilisant la boîte de dialogue **Éditeur d’associations**.

 Vous devez sélectionner une classe parente et une classe enfant quand vous utilisez la boîte de dialogue **Éditeur d’associations** pour créer une association. La classe parente est la classe d'entité qui contient la clé primaire ; la classe enfant est la classe d'entité qui contient la clé étrangère. Par exemple, si les classes d'entité ont été créées pour mapper aux tables Customers et Orders de Northwind, la classe Customer constitue la classe parente et la classe Order, la classe enfant.

> [!NOTE]
> Lorsque vous faites glisser des tables à partir de **Explorateur de serveurs** /**explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), les associations sont créées automatiquement en fonction des relations de clé étrangère existantes dans la base de données.

 Une fois que vous avez créé une association, lorsque vous sélectionnez l’Association dans le Concepteur O/R, certaines propriétés peuvent être configurées dans la fenêtre **Propriétés** . (L’Association est la ligne entre les classes connexes.) Le tableau suivant fournit des descriptions pour les propriétés d’une association.

|Property|Description|
|--------------|-----------------|
|**Cardinalité**|Détermine s'il s'agit d'une l'association est un-à-plusieurs ou un-à-un.|
|**Propriété enfant**|Spécifie s’il faut créer, dans le parent, une propriété qui est une collection ou une référence aux enregistrements enfants sur le côté clé étrangère de l’association. Par exemple, dans l’association entre Customer et Order, si la **propriété Child** a la valeur **true**, une propriété nommée Orders est créée sur la classe parente.|
|**Propriété parent**|Propriété de la classe enfant qui fait référence à la classe parente associée. Par exemple, dans l'association entre Customer et Order, une propriété nommée Customer qui fait référence au client associé à une commande est créée dans la classe Order.|
|**Propriétés participantes**|Affiche les propriétés d’association et fournit un bouton de **sélection** (…) qui rouvre la boîte de dialogue **Éditeur d’associations**.|
|**Unique**|Spécifie si les colonnes cibles étrangères ont une contrainte d'unicité.|

### <a name="to-create-an-association-between-entity-classes"></a>Pour créer une association entre des classes d'entité

1. Cliquez avec le bouton droit sur la classe d’entité qui représente la classe parente dans l’association, pointez sur **Ajouter**, puis cliquez sur **Association**.

2. Vérifiez que la **Classe parente** correcte est sélectionnée dans la boîte de dialogue **Éditeur d’associations**.

3. Sélectionnez la **Classe enfant** dans la zone de liste déroulante.

4. Sélectionnez les **Propriétés d’association** qui lient les classes. En général, un mappage à la relation de clé étrangère définie dans la base de données est alors établi. Par exemple, dans l’Association Customers et Orders, les **propriétés d’association** sont CustomerID pour chaque classe.

5. Cliquez sur **OK** pour créer l’association.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procédure pas à pas : création de classes LINQ to SQL (concepteur o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [méthodes DataContext (concepteur o/r)](../data-tools/datacontext-methods-o-r-designer.md) [Comment : représenter des clés primaires](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
