---
title: 'Comment : modifier le type de retour d’une méthode DataContext (Concepteur O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089355"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)
Le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode) (créée en fonction d’une procédure stockée ou une fonction) diffère selon l’endroit où vous placez la procédure stockée ou fonction dans le **Concepteur O/R**. Si vous déposez directement un élément sur une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> ayant le type de retour de la classe d'entité est créée (si le schéma des données a été retourné par la procédure stockée ou si la fonction correspond à la forme de la classe d'entité). Si vous déposez un élément dans une zone vide de la **Concepteur O/R**, un <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode), sélectionnez-la et cliquez sur le **Type de retour** propriété dans le **propriétés** fenêtre.

> [!NOTE]
>  Vous ne pouvez pas annuler <xref:System.Data.Linq.DataContext> méthodes qui ont un type de retour pour une classe d’entité pour retourner le type généré automatiquement en utilisant le **propriétés** fenêtre. Pour rétablir une <xref:System.Data.Linq.DataContext> méthode pour retourner un type généré automatiquement, vous devez faire glisser l’objet de base de données d’origine sur le **Concepteur O/R** à nouveau.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Pour modifier le type de retour d’une méthode DataContext du type généré automatiquement vers une classe d’entité

1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes.

2.  Sélectionnez **Type de retour** dans le **propriétés** fenêtre et sélectionnez une entité disponible classe dans le **Type de retour** liste. Si la classe d’entité souhaitée n’est pas dans la liste, ajoutez-la ou créez-la dans le **Concepteur O/R** pour l’ajouter à la liste.

3.  Enregistrer le *.dbml* fichier.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Pour modifier le type de retour d’une méthode DataContext d’une classe d’entité vers le type généré automatiquement

1.  Sélectionnez le <xref:System.Data.Linq.DataContext> méthode dans le **méthodes** volet et supprimez-le.

2.  Faites glisser l’objet de base de données à partir de **Explorateur de serveurs** ou **Database Explorer** dans une zone vide de la **Concepteur O/R**.

3.  Enregistrer le *.dbml* fichier.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)