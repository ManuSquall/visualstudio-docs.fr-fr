---
title: 'Procédure : modifier le type de retour d’une méthode DataContext (Concepteur O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 77d7b98367e343f90827429ad50be91527f7f303
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939435"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procédure : modifier le type de retour d’une méthode DataContext (Concepteur O/R)
Le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode) (créée en fonction d’une procédure stockée ou une fonction) diffère selon l’endroit où vous placez la procédure stockée ou fonction dans le **Concepteur O/R**. Si vous déposez directement un élément sur une classe d’entité existante, une méthode <xref:System.Data.Linq.DataContext> ayant le type de retour de la classe d’entité est créée (si le schéma des données a été retourné par la procédure stockée ou si la fonction correspond à la forme de la classe d’entité). Si vous déposez un élément dans une zone vide de la **Concepteur O/R**, un <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et cliquez sur la propriété **Type de retour** dans la fenêtre **Propriétés**.

> [!NOTE]
>  Vous ne pouvez pas rétablir les méthodes <xref:System.Data.Linq.DataContext> dont le jeu de types de retour est une classe d’entité afin de retourner le type généré automatiquement via la fenêtre **Propriétés**. Pour rétablir une méthode <xref:System.Data.Linq.DataContext> afin de retourner un type généré automatiquement, vous devez faire glisser une nouvelle fois l’objet de base de données d’origine vers le **Concepteur O/R**.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Pour modifier le type de retour d’une méthode DataContext du type généré automatiquement vers une classe d’entité

1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes.

2.  Sélectionnez **Type de retour** dans la fenêtre **Propriétés**, puis sélectionnez une classe d’entité disponible dans la liste **Type de retour**. Si la classe d’entité souhaitée n’est pas dans la liste, ajoutez-la ou créez-la dans le **Concepteur O/R** pour l’ajouter à la liste.

3.  Enregistrez le fichier *.dbml*.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Pour modifier le type de retour d’une méthode DataContext d’une classe d’entité vers le type généré automatiquement

1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet **Méthodes** et supprimez-la.

2.  Faites glisser l’objet de base de données à partir de **Explorateur de serveurs** ou **Database Explorer** dans une zone vide de la **Concepteur O/R**.

3.  Enregistrez le fichier *.dbml*.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)