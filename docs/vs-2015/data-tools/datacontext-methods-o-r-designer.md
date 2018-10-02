---
title: Méthodes DataContext (Concepteur O-R) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fd44dbfa9a39afafa22965e77ad87f8f243b9ae3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516607"
---
# <a name="datacontext-methods-or-designer"></a>DataContext, méthodes (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [DataContext, méthodes (Concepteur O-R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer).  
  
  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) méthodes (dans le contexte de la [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sont des méthodes de la <xref:System.Data.Linq.DataContext> classe qui s’exécutent stockée les procédures et fonctions dans une base de données.  
  
 La classe <xref:System.Data.Linq.DataContext> est une classe [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] qui agit comme un conduit entre une base de données SQL Server et les classes d'entité [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] mappées à cette base de données. La classe <xref:System.Data.Linq.DataContext> contient les informations de chaîne de connexion et les méthodes pour se connecter à une base de données et manipuler les données dans celle-ci. Par défaut, la classe <xref:System.Data.Linq.DataContext> contient plusieurs méthodes que vous pouvez appeler, telles que la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> qui envoie des données mises à jour des classes [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] vers la base de données. Vous pouvez également créer d’autres <xref:System.Data.Linq.DataContext> méthodes qui mappent aux procédures stockées et fonctions. En d'autres termes, l'appel de ces méthodes personnalisées exécutera la procédure stockée ou la fonction dans la base de données à laquelle la méthode <xref:System.Data.Linq.DataContext> est mappée. Vous pouvez ajouter de nouvelles méthodes à la classe <xref:System.Data.Linq.DataContext> en procédant comme pour l'ajout de toute autre méthode destinée à étendre une classe. Toutefois, des discussions sur <xref:System.Data.Linq.DataContext> méthodes dans le contexte de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], il est le <xref:System.Data.Linq.DataContext> méthodes qui mappent aux procédures stockées et fonctions qui sont examinées.  
  
## <a name="methods-pane"></a>Volet de méthodes  
 Les méthodes <xref:System.Data.Linq.DataContext> qui mappent aux procédures stockées et aux fonctions sont affichées dans le volet de méthodes du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Le volet de méthodes est le volet le long du côté de la **entités** volet (l’aire de conception principale). Le volet de méthodes répertorie tous les <xref:System.Data.Linq.DataContext> méthodes que vous avez créé à l’aide de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Par défaut, le volet de méthodes est vide. Faites glisser des procédures stockées ou des fonctions de **Explorateur de serveurs**/**Database Explorer** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] pour créer <xref:System.Data.Linq.DataContext> méthodes et remplir le volet de méthodes. Pour plus d’informations, consultez [Comment : créer un DataContext, méthodes mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Ouvrir et fermer le volet de méthodes en double-cliquant sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , puis en cliquant sur **masquer le volet méthodes** ou **afficher le volet méthodes**, ou utilisez le raccourci clavier CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Deux types de méthodes DataContext  
 Les méthodes DataContext sont les méthodes qui mappent aux procédures stockées et aux fonctions dans la base de données. Vous pouvez créer et ajouter des méthodes DataContext dans le volet de méthodes du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il existe deux types distincts de <xref:System.Data.Linq.DataContext> méthodes ; celles qui retournent un ou plusieurs jeux de résultats et celles qui ne le faites pas :  
  
-   Méthodes <xref:System.Data.Linq.DataContext> qui retournent un ou plusieurs jeux de résultats :  
  
     Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit juste exécuter des procédures stockées et des fonctions dans la base de données et retourner les résultats. Pour plus d’informations, consultez [Comment : créer un DataContext, méthodes mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, et <xref:System.Data.Linq.IMultipleResults>.  
  
-   Méthodes <xref:System.Data.Linq.DataContext> qui ne retournent aucun jeu de résultats, par exemple celles qui effectuent des insertions, des mises à jour et des suppressions pour une classe d'entité spécifique.  
  
     Créez ce type de <xref:System.Data.Linq.DataContext> méthode quand votre application doit exécuter des procédures stockées au lieu d’utiliser la valeur par défaut [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] comportement pour l’enregistrement de données entre une classe d’entité et de la base de données modifiées. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Types de retour des méthodes DataContext  
 Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs**/**Database Explorer** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], le type de retour de généré <xref:System.Data.Linq.DataContext> diffère de la méthode selon l’endroit où vous placez l’élément. Suppression d’éléments directement sur une classe d’entité existante crée une <xref:System.Data.Linq.DataContext> méthode avec le type de retour de la classe d’entité ; placer des éléments dans une zone vide de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (dans le volet) crée un <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement. Le type généré automatiquement possède un nom correspondant au nom de la procédure stockée ou de la fonction et des propriétés qui mappent aux champs retournés par la procédure stockée ou fonction.  
  
> [!NOTE]
>  Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’un <xref:System.Data.Linq.DataContext> (méthode), sélectionnez-la et inspectez le **Type de retour** propriété dans le **propriétés** fenêtre. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Les objets que vous faites glisser de la base de données vers l'aire du Concepteur O/R sont nommés automatiquement, en fonction du nom des objets dans la base de données. Lorsque vous faites glisser plusieurs fois le même objet, un numéro est ajouté à la fin du nouveau nom afin de différencier les noms. Lorsque les noms des objets de la base de données contiennent des espaces ou des caractères non pris en charge en Visual Basic ou en C#, l'espace ou le caractère non valide est remplacé par un trait de soulignement.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Procédures stockées](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Procédure pas à pas : Personnalisation de l’insertion, mise à jour et supprimer le comportement des classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)

