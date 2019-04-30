---
title: Comment créer une relation entre les classes LINQ to SQL à l’aide du Concepteur O/R
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b6f0b1f3afec1231778a54c82422d6761995eb1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402792"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Procédure : Créer une association entre les classes LINQ to SQL (Concepteur O/R)
Les associations entre classes d'entité dans [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sont analogues aux relations entre les tables dans une base de données. Vous pouvez créer des associations entre des classes d’entité en utilisant la boîte de dialogue **Éditeur d’associations**.

Vous devez sélectionner une classe parente et une classe enfant quand vous utilisez la boîte de dialogue **Éditeur d’associations** pour créer une association. La classe parente est la classe d'entité qui contient la clé primaire ; la classe enfant est la classe d'entité qui contient la clé étrangère. Par exemple, si les classes d’entité ont été créées pour mapper à la `Northwind Customers` et `Orders` tables, les `Customer` classe serait la classe parente et le `Order` classe serait la classe enfant.

> [!NOTE]
> Lorsque vous faites glisser les tables à partir de **Explorateur de serveurs** ou **Database Explorer** sur le **concepteur objet/relationnel** (**Concepteur O/R**), associations sont créées automatiquement selon les relations de clé étrangère existantes dans la base de données.

## <a name="association-properties"></a>Propriétés d’association
Après avoir créé une association, quand vous sélectionnez l’association dans le **Concepteur O/R**, la fenêtre **Propriétés** contient des propriétés configurables. (L'association est la ligne entre les classes connexes.) Le tableau suivant décrit les propriétés d'une association.

|Propriété|Description|
|--------------|-----------------|
|**Cardinalité**|Détermine s'il s'agit d'une l'association est un-à-plusieurs ou un-à-un.|
|**Propriété enfant**|Spécifie s’il faut créer, dans le parent, une propriété qui est une collection ou une référence aux enregistrements enfants sur le côté clé étrangère de l’association. Par exemple, dans l’association entre `Customer` et `Order`, si le **propriété enfant** a la valeur **True**, une propriété nommée `Orders` est créée sur la classe parente.|
|**Propriété parent**|Propriété de la classe enfant qui fait référence à la classe parente associée. Par exemple, dans l’association entre `Customer` et `Order`, une propriété nommée `Customer` qui fait référence au client associé à une commande est créé sur le `Order` classe.|
|**Propriétés participantes**|Affiche les propriétés d’association et fournit un bouton de **sélection** (…) qui rouvre la boîte de dialogue **Éditeur d’associations**.|
|**Unique**|Spécifie si les colonnes cibles étrangères ont une contrainte d'unicité.|

## <a name="to-create-an-association-between-entity-classes"></a>Pour créer une association entre des classes d'entité

1. Cliquez avec le bouton droit sur la classe d’entité qui représente la classe parente dans l’association, pointez sur **Ajouter**, puis cliquez sur **Association**.

2. Vérifiez que la **Classe parente** correcte est sélectionnée dans la boîte de dialogue **Éditeur d’associations**.

3. Sélectionnez la **Classe enfant** dans la zone de liste déroulante.

4. Sélectionnez les **Propriétés d’association** qui lient les classes. En général, un mappage à la relation de clé étrangère définie dans la base de données est alors établi. Par exemple, dans le `Customers` et `Orders` association, le **propriétés d’Association** sont la `CustomerID` pour chaque classe.

5. Cliquez sur **OK** pour créer l’association.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de LINQ aux classes SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour Représenter les clés primaires](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)