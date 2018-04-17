---
title: 'Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O-R) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d57d467acb279a74f35703ea176e4a726ccbbe96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)
Procédures stockées et fonctions peuvent être ajoutées à la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] comme <xref:System.Data.Linq.DataContext> méthodes. Appel de la méthode et en passant les paramètres requis s’exécute la procédure stockée ou fonction dans la base de données et renvoie les données dans le type de retour de la <xref:System.Data.Linq.DataContext> (méthode). Pour plus d’informations sur les <xref:System.Data.Linq.DataContext> méthodes, consultez [des méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Les procédures stockées peuvent également être utilisées pour substituer le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui effectue des insertions, des mises à jour et des suppressions lorsque les modifications sont enregistrées des classes d'entité vers une base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Création de méthodes DataContext  
 Vous pouvez créer <xref:System.Data.Linq.DataContext> méthodes en faisant glisser des procédures stockées ou fonctions de **Server Explorer/Database Explorer** sur la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Le type de retour de la méthode <xref:System.Data.Linq.DataContext> générée diffère selon l'endroit où vous placez la procédure stockée ou fonction dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Le déplacement direct des éléments vers une classe d'entité existante crée une méthode <xref:System.Data.Linq.DataContext> avec le type de retour de la classe d'entité. Le déplacement d'éléments vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crée une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement. Vous pouvez modifier le type de retour d’un <xref:System.Data.Linq.DataContext> méthode après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode), sélectionnez-la et inspectez le **Type de retour** propriété dans le **propriétés** fenêtre. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Pour créer des méthodes DataContext qui retournent automatiquement les types générés  
  
1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez le **de procédures stockées** nœud de la base de données que vous utilisez.  
  
2.  Localisez la procédure stockée requise et faites-la glisser vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Le <xref:System.Data.Linq.DataContext> (méthode) est créée avec un type de retour généré automatiquement et apparaît dans le **méthodes** volet.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Pour créer des méthodes DataContext qui ont le type de retour d’une classe d’entité  
  
1.  Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez le **de procédures stockées** nœud de la base de données que vous utilisez.  
  
2.  Localisez la procédure stockée requise et faites-la glisser sur une classe d'entité existante dans le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Le <xref:System.Data.Linq.DataContext> (méthode) est créée avec le type de retour de la classe d’entité sélectionnée et apparaît dans le **méthodes** volet.  
  
> [!NOTE]
>  Pour plus d’informations sur la modification du type de retour d’existant <xref:System.Data.Linq.DataContext> méthodes, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Introduction à LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ en C#](/dotnet/csharp/linq/linq-in-csharp)