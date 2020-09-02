---
title: Méthodes DataContext (Concepteur O-R) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657394"
---
# <a name="datacontext-methods-or-designer"></a>DataContext, méthodes (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///T : System. Data. Linq. DataContext ? qualifyHint = false&les méthodes AutoUpgrade = true) (dans le contexte des [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sont des méthodes de la <xref:System.Data.Linq.DataContext> classe qui exécutent des procédures stockées et des fonctions dans une base de données.

 La classe <xref:System.Data.Linq.DataContext> est une classe [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] qui agit comme un conduit entre une base de données SQL Server et les classes d'entité [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] mappées à cette base de données. La classe <xref:System.Data.Linq.DataContext> contient les informations de chaîne de connexion et les méthodes pour se connecter à une base de données et manipuler les données dans celle-ci. Par défaut, la classe <xref:System.Data.Linq.DataContext> contient plusieurs méthodes que vous pouvez appeler, telles que la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> qui envoie des données mises à jour des classes [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] vers la base de données. Vous pouvez également créer des méthodes <xref:System.Data.Linq.DataContext> supplémentaires pour mapper aux procédures stockées et aux fonctions. En d'autres termes, l'appel de ces méthodes personnalisées exécutera la procédure stockée ou la fonction dans la base de données à laquelle la méthode <xref:System.Data.Linq.DataContext> est mappée. Vous pouvez ajouter de nouvelles méthodes à la classe <xref:System.Data.Linq.DataContext> en procédant comme pour l'ajout de toute autre méthode destinée à étendre une classe. Toutefois, dans les discussions sur les <xref:System.Data.Linq.DataContext> méthodes dans le contexte du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , il s’agit des <xref:System.Data.Linq.DataContext> méthodes qui mappent aux procédures stockées et aux fonctions qui sont discutées.

## <a name="methods-pane"></a>Volet de méthodes
 <xref:System.Data.Linq.DataContext> les méthodes qui mappent aux procédures stockées et aux fonctions sont affichées dans le volet de méthodes de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Le volet de méthodes est le volet situé sur le côté du volet **entités** (l’aire de conception principale). Le volet méthodes répertorie toutes les <xref:System.Data.Linq.DataContext> méthodes que vous avez créées à l’aide de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Par défaut, le volet de méthodes est vide. Faites glisser des procédures stockées ou des fonctions de **Explorateur de serveurs** / **Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] pour créer <xref:System.Data.Linq.DataContext> des méthodes et remplir le volet de méthodes. Pour plus d’informations, consultez [Comment : créer des méthodes DataContext mappées à des procédures stockées et des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Ouvrez et fermez le volet méthodes en cliquant avec le bouton droit sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , puis en cliquant sur **masquer le volet méthodes** ou **afficher le volet méthodes**, ou utilisez le raccourci clavier CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Deux types de méthodes DataContext
 Les méthodes DataContext sont les méthodes qui mappent aux procédures stockées et aux fonctions dans la base de données. Vous pouvez créer et ajouter des méthodes DataContext dans le volet de méthodes du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il existe deux types distincts de méthodes <xref:System.Data.Linq.DataContext> : celles qui retournent un ou plusieurs jeux de résultats et celles qui ne retournent aucun jeu de résultats :

- Méthodes <xref:System.Data.Linq.DataContext> qui retournent un ou plusieurs jeux de résultats :

     Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit juste exécuter des procédures stockées et des fonctions dans la base de données et retourner les résultats. Pour plus d’informations, consultez [Comment : créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. Linq. ISingleResult \<T> et <xref:System.Data.Linq.IMultipleResults> .

- Méthodes <xref:System.Data.Linq.DataContext> qui ne retournent aucun jeu de résultats, par exemple celles qui effectuent des insertions, des mises à jour et des suppressions pour une classe d'entité spécifique.

     Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit exécuter des procédures stockées au lieu d’utiliser le comportement [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] par défaut pour enregistrer des données modifiées entre une classe d’entité et la base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Types de retour des méthodes DataContext
 Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs** / **Explorateur de base de données** vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , le type de retour de la <xref:System.Data.Linq.DataContext> méthode générée diffère selon l’endroit où vous déposez l’élément. La suppression directe des éléments dans une classe d’entité existante crée une <xref:System.Data.Linq.DataContext> méthode avec le type de retour de la classe d’entité ; la suppression d’éléments dans une zone vide du [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (dans l’un ou l’autre volet) crée une <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement. Le type généré automatiquement possède un nom correspondant au nom de la procédure stockée ou de la fonction et des propriétés qui mappent aux champs retournés par la procédure stockée ou fonction.

> [!NOTE]
> Vous pouvez modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext> après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Les objets que vous faites glisser de la base de données vers l'aire du Concepteur O/R sont nommés automatiquement, en fonction du nom des objets dans la base de données. Lorsque vous faites glisser plusieurs fois le même objet, un numéro est ajouté à la fin du nouveau nom afin de différencier les noms. Lorsque les noms des objets de la base de données contiennent des espaces ou des caractères non pris en charge en Visual Basic ou en C#, l'espace ou le caractère non valide est remplacé par un trait de soulignement.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procédures stockées](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [Comment : créer des méthodes DataContext mappées à des procédures stockées et des fonctions (concepteur o/r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (concepteur o/](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) r) procédure [pas à pas : personnalisation du comportement d’insertion, LINQ to SQL de mise à jour et de suppression](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [Walkthrough: Creating LINQ to SQL Classes (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
