---
title: 'Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O-R) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62d250946e634627c16dbd3b56fce370c11e1f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502529"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : créer un DataContext, méthodes mappées aux procédures stockées et fonctions (Concepteur O-R)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer).  
  
  
Procédures stockées et fonctions peuvent être ajoutées à la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] comme <xref:System.Data.Linq.DataContext> méthodes. Appel de la méthode et en passant les paramètres requis s’exécute la procédure stockée ou la fonction sur la base de données et renvoie les données dans le type de retour de la <xref:System.Data.Linq.DataContext> (méthode). Pour plus d’informations sur <xref:System.Data.Linq.DataContext> méthodes, consultez [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Les procédures stockées peuvent également être utilisées pour substituer le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] qui effectue des insertions, des mises à jour et des suppressions lorsque les modifications sont enregistrées des classes d'entité vers une base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Création de méthodes DataContext  
 Vous pouvez créer <xref:System.Data.Linq.DataContext> méthodes en faisant glisser des procédures stockées ou fonctions de **Server Explorer/Database Explorer** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Le type de retour de la méthode <xref:System.Data.Linq.DataContext> générée diffère selon l'endroit où vous placez la procédure stockée ou fonction dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Le déplacement direct des éléments vers une classe d'entité existante crée une méthode <xref:System.Data.Linq.DataContext> avec le type de retour de la classe d'entité. Le déplacement d'éléments vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crée une méthode <xref:System.Data.Linq.DataContext> qui retourne un type généré automatiquement. Vous pouvez modifier le type de retour d’un <xref:System.Data.Linq.DataContext> méthode après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode), sélectionnez-la et inspectez le **Type de retour** propriété dans le **propriétés** fenêtre. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Pour créer des méthodes DataContext qui retournent automatiquement les types générés  
  
1.  Dans **Explorateur de serveurs**/**l’Explorateur de base de données**, développez le **Stored Procedures** nœud de la base de données que vous utilisez.  
  
2.  Localisez la procédure stockée requise et faites-la glisser vers une zone vide dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Le <xref:System.Data.Linq.DataContext> méthode est créée avec un type de retour généré automatiquement et apparaît dans le **méthodes** volet.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Pour créer des méthodes DataContext qui ont le type de retour d’une classe d’entité  
  
1.  Dans **Explorateur de serveurs**/**l’Explorateur de base de données**, développez le **Stored Procedures** nœud de la base de données que vous utilisez.  
  
2.  Localisez la procédure stockée requise et faites-la glisser sur une classe d'entité existante dans le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Le <xref:System.Data.Linq.DataContext> méthode est créée avec le type de retour de la classe d’entité sélectionnée et apparaît dans le **méthodes** volet.  
  
> [!NOTE]
>  Pour plus d’informations sur la modification du type de retour d’existant <xref:System.Data.Linq.DataContext> méthodes, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Introduction à LINQ en Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Comment : écrire des requêtes LINQ en C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

