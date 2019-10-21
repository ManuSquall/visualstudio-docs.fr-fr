---
title: Relations entre les classes LINQ to SQL (Concepteur O/R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13443dd25719caad5002b29a33975a0dbc5850f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641900"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Comment : créer une association entre des classes LINQ to SQL (Concepteur O/R)
Les associations entre classes d'entité dans [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sont analogues aux relations entre les tables dans une base de données. Vous pouvez créer des associations entre des classes d’entité en utilisant la boîte de dialogue **Éditeur d’associations**.

Vous devez sélectionner une classe parente et une classe enfant quand vous utilisez la boîte de dialogue **Éditeur d’associations** pour créer une association. La classe parente est la classe d'entité qui contient la clé primaire ; la classe enfant est la classe d'entité qui contient la clé étrangère. Par exemple, si des classes d’entité qui mappent aux tables `Northwind Customers` et `Orders`, la classe `Customer` serait la classe parente et la classe `Order` serait la classe enfant.

> [!NOTE]
> Lorsque vous faites glisser des tables à partir de **Explorateur de serveurs** ou **explorateur de base de données** vers le **Concepteur Objet Relationnel** (**Concepteur O/R**), les associations sont créées automatiquement en fonction des relations de clé étrangère existantes dans la base de données.

## <a name="association-properties"></a>Propriétés d’association
Après avoir créé une association, quand vous sélectionnez l’association dans le **Concepteur O/R**, la fenêtre **Propriétés** contient des propriétés configurables. (L’Association est la ligne entre les classes connexes.) Le tableau suivant fournit des descriptions pour les propriétés d’une association.

|Property|Description|
|--------------|-----------------|
|**Cardinalité**|Détermine s'il s'agit d'une l'association est un-à-plusieurs ou un-à-un.|
|**Propriété enfant**|Spécifie s’il faut créer, dans le parent, une propriété qui est une collection ou une référence aux enregistrements enfants sur le côté clé étrangère de l’association. Par exemple, dans l’association entre `Customer` et `Order`, si la **propriété enfant** est définie sur **true**, une propriété nommée `Orders` est créée sur la classe parente.|
|**Propriété parent**|Propriété de la classe enfant qui fait référence à la classe parente associée. Par exemple, dans l’association entre `Customer` et `Order`, une propriété nommée `Customer` qui fait référence au client associé pour une commande est créée sur la classe `Order`.|
|**Propriétés participantes**|Affiche les propriétés d’association et fournit un bouton de **sélection** (…) qui rouvre la boîte de dialogue **Éditeur d’associations**.|
|**Unique**|Spécifie si les colonnes cibles étrangères ont une contrainte d'unicité.|

## <a name="to-create-an-association-between-entity-classes"></a>Pour créer une association entre des classes d'entité

1. Cliquez avec le bouton droit sur la classe d’entité qui représente la classe parente dans l’association, pointez sur **Ajouter**, puis cliquez sur **Association**.

2. Vérifiez que la **Classe parente** correcte est sélectionnée dans la boîte de dialogue **Éditeur d’associations**.

3. Sélectionnez la **Classe enfant** dans la zone de liste déroulante.

4. Sélectionnez les **Propriétés d’association** qui lient les classes. En général, un mappage à la relation de clé étrangère définie dans la base de données est alors établi. Par exemple, dans l’Association `Customers` et `Orders`, les **propriétés d’association** sont les `CustomerID` pour chaque classe.

5. Cliquez sur **OK** pour créer l’association.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : création de classes LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour représenter les clés primaires](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
