---
title: Comment créer une relation entre les classes LINQ to SQL à l’aide du Concepteur O/R
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9eb6237af696dc1f56ae82bd99a1ddfc54851484
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Comment : créer une association entre les classes LINQ to SQL (Concepteur O/R)
Les associations entre classes d'entité dans [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sont analogues aux relations entre les tables dans une base de données. Vous pouvez créer des associations entre classes d’entité à l’aide de la **Éditeur d’associations** boîte de dialogue.

Vous devez sélectionner une classe parente et la classe enfant lorsque vous utilisez la **Éditeur d’associations** boîte de dialogue pour créer une association. La classe parente est la classe d'entité qui contient la clé primaire ; la classe enfant est la classe d'entité qui contient la clé étrangère. Par exemple, si les classes d'entité ont été créées pour mapper aux tables Customers et Orders de Northwind, la classe Customer constitue la classe parente et la classe Order, la classe enfant.

> [!NOTE]
>  Lorsque vous faites glisser les tables à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), associations sont créées automatiquement en fonction de l’existant relations de clé étrangère dans la base de données.

## <a name="association-properties"></a>Propriétés d’association
Après avoir créé une association, lorsque vous sélectionnez l’association dans le Concepteur O/R, il existe des propriétés configurables dans le **propriétés** fenêtre. (L'association est la ligne entre les classes connexes.) Le tableau suivant décrit les propriétés d'une association.

|Propriété|Description|
|--------------|-----------------|
|**Cardinalité**|Détermine s'il s'agit d'une l'association est un-à-plusieurs ou un-à-un.|
|**Propriété enfant**|Spécifie s’il faut créer, dans le parent, une propriété qui est une collection ou une référence aux enregistrements enfants sur le côté clé étrangère de l’association. Par exemple, dans l’association entre Customer et Order, si le **propriété enfant** a la valeur **True**, une propriété nommée Orders est créée dans la classe parente.|
|**Propriété parent**|Propriété de la classe enfant qui fait référence à la classe parente associée. Par exemple, dans l'association entre Customer et Order, une propriété nommée Customer qui fait référence au client associé à une commande est créée dans la classe Order.|
|**Propriétés participantes**|Affiche les propriétés d’associations et fournit un **points de suspension** bouton (...) qui ouvre le **Éditeur d’associations** boîte de dialogue.|
|**Unique**|Spécifie si les colonnes cibles étrangères ont une contrainte d'unicité.|

## <a name="to-create-an-association-between-entity-classes"></a>Pour créer une association entre des classes d'entité

1.  Avec le bouton droit de la classe d’entité qui représente la classe parente dans l’association, pointez sur **ajouter**, puis cliquez sur **Association**.

2.  Vérifiez que le bon **classe parente** est sélectionné dans le **Éditeur d’associations** boîte de dialogue.

3.  Sélectionnez le **classe enfant** dans la zone de liste déroulante.

4.  Sélectionnez le **propriétés d’Association** qui lient les classes. En général, un mappage à la relation de clé étrangère définie dans la base de données est alors établi. Par exemple, dans les associations Customers et Orders, la **propriétés d’Association** sont les CustomerID pour chaque classe.

5.  Cliquez sur **OK** pour créer l’association.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création des Classes LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour représenter les clés primaires](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)