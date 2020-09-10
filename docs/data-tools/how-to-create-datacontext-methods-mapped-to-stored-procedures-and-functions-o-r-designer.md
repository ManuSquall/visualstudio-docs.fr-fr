---
title: Mapper des méthodes DataContext à des sprocs et des fonctions
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 21ea455e6cc29d17f9050e54dd2f8d11033320ac
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742897"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)

Vous pouvez ajouter des procédures stockées et des fonctions au **Concepteur O/R** en tant que <xref:System.Data.Linq.DataContext> méthodes. En appelant la méthode pour passer les paramètres requis, la procédure stockée ou fonction est exécutée sur la base de données et retourne les données dans le type de retour de la méthode <xref:System.Data.Linq.DataContext>. Pour plus d’informations sur les <xref:System.Data.Linq.DataContext> méthodes, consultez [méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Vous pouvez également utiliser des procédures stockées pour remplacer le comportement par défaut au moment de l' [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] exécution qui effectue des insertions, des mises à jour et des suppressions lorsque des modifications sont enregistrées à partir de classes d’entité dans une base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Créer des méthodes DataContext

Vous pouvez créer des <xref:System.Data.Linq.DataContext> méthodes en faisant glisser des procédures stockées ou des fonctions à partir de <strong>Explorateur de serveurs ou * * Explorateur de base de données</strong> vers le **Concepteur O/R**.

> [!NOTE]
> Le type de retour de la <xref:System.Data.Linq.DataContext> méthode générée diffère selon l’endroit où vous déposez la procédure stockée ou la fonction dans le **Concepteur O/R**. Le déplacement direct des éléments vers une classe d'entité existante crée une méthode <xref:System.Data.Linq.DataContext> avec le type de retour de la classe d'entité. La suppression d’éléments dans une zone vide du **Concepteur O/R** crée une <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement. Vous pouvez modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext> après l’avoir ajoutée au volet **Méthodes**. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Pour créer des méthodes DataContext qui retournent automatiquement les types générés

1. Dans **Explorateur de serveurs** ou **Explorateur de base de données**, développez le nœud **procédures stockées** de la base de données avec laquelle vous travaillez.

2. Localisez la procédure stockée souhaitée et faites-la glisser sur une zone vide du **Concepteur O/R**.

     La méthode <xref:System.Data.Linq.DataContext> est créée avec un type de retour généré automatiquement et apparaît dans le volet **Méthodes**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Pour créer des méthodes DataContext qui ont le type de retour d'une classe d'entité

1. Dans **Explorateur de serveurs** ou **Explorateur de base de données**, développez le nœud **procédures stockées** de la base de données avec laquelle vous travaillez.

2. Localisez la procédure stockée souhaitée et faites-la glisser sur une classe d’entité existante dans le **Concepteur O/R**.

     La méthode <xref:System.Data.Linq.DataContext> est créée avec le type de retour de la classe d’entité sélectionnée et apparaît dans le volet **Méthodes**.

> [!NOTE]
> Pour plus d’informations sur la modification du type de retour d’existant <xref:System.Data.Linq.DataContext> méthodes, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Méthode DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procédure pas à pas : création de classes LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduction à LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ en C#](/dotnet/csharp/linq/linq-in-csharp)
