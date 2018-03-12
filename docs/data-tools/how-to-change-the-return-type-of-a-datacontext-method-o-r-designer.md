---
title: "Comment : modifier le type de retour d’une méthode DataContext (Concepteur O-R) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: e086747d859e1e3306d9f42fbe296d144954382f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)
Le type de retour d'une méthode <xref:System.Data.Linq.DataContext> (créée selon une procédure stockée ou fonction) diffère selon l'endroit où vous placez la procédure stockée ou la fonction dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si vous déposez directement un élément sur une classe d'entité existante, une méthode <xref:System.Data.Linq.DataContext> ayant le type de retour de la classe d'entité est créée (si le schéma des données a été retourné par la procédure stockée ou si la fonction correspond à la forme de la classe d'entité). Si vous déposez un élément dans une zone vide du [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement est créée. Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> méthode, sélectionnez-la, puis cliquez sur le **Type de retour** propriété dans le **propriétés** fenêtre.  
  
> [!NOTE]
>  Vous ne pouvez pas rétablir <xref:System.Data.Linq.DataContext> méthodes qui ont un type de retour d’une classe d’entité pour retourner le type généré automatiquement en utilisant le **propriétés** fenêtre. Pour rétablir une méthode <xref:System.Data.Linq.DataContext> afin de retourner un type généré automatiquement, vous devez faire glisser l'objet de base de données d'origine vers le Concepteur O/R.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Pour modifier le type de retour d'une méthode DataContext du type généré automatiquement vers une classe d'entité  
  
1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes.  
  
2.  Sélectionnez **Type de retour** dans les **propriétés** classe de fenêtre et sélectionnez une entité disponible dans le **Type de retour** liste. Si la classe d’entité souhaité n’est pas dans la liste, ajoutez-la ou créez-la dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] pour l’ajouter à la liste.  
  
3.  Enregistrez le fichier .dbml.  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Pour modifier le type de retour d'une méthode DataContext d'une classe d'entité vers le type généré automatiquement  
  
1.  Sélectionnez la méthode <xref:System.Data.Linq.DataContext> dans le volet de méthodes et supprimez-la.  
  
2.  Faites glisser l’objet de base de données à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** dans une zone vide du Concepteur O/R.  
  
3.  Enregistrez le fichier .dbml.  
  
## <a name="see-also"></a>Voir aussi
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
[Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)