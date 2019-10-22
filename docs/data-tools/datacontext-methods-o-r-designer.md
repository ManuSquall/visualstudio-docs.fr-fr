---
title: DataContext, méthodes (Concepteur O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0e81f2337931f565e0068a852bf9b8284350690c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648539"
---
# <a name="datacontext-methods-or-designer"></a>DataContext, méthodes (Concepteur O/R)

<xref:System.Data.Linq.DataContext> méthodes (dans le contexte des [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sont des méthodes de la classe <xref:System.Data.Linq.DataContext> qui exécutent des procédures stockées et des fonctions dans une base de données.

La classe <xref:System.Data.Linq.DataContext> est une classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui agit comme un conduit entre une base de données SQL Server et les classes d'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] mappées à cette base de données. La classe <xref:System.Data.Linq.DataContext> contient les informations de chaîne de connexion et les méthodes pour se connecter à une base de données et manipuler les données dans celle-ci. Par défaut, la classe <xref:System.Data.Linq.DataContext> contient plusieurs méthodes que vous pouvez appeler, telles que la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> qui envoie des données mises à jour des classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] vers la base de données. Vous pouvez également créer des méthodes <xref:System.Data.Linq.DataContext> supplémentaires pour mapper aux procédures stockées et aux fonctions. En d’autres termes, l’appel de ces méthodes personnalisées exécute la procédure stockée ou la fonction dans la base de données à laquelle la méthode <xref:System.Data.Linq.DataContext> est mappée. Vous pouvez ajouter de nouvelles méthodes à la classe <xref:System.Data.Linq.DataContext> en procédant comme pour l'ajout de toute autre méthode destinée à étendre une classe. Toutefois, dans les discussions sur les méthodes de <xref:System.Data.Linq.DataContext> dans le contexte du **Concepteur O/R**, il s’agit des méthodes <xref:System.Data.Linq.DataContext> qui mappent aux procédures stockées et aux fonctions qui sont discutées.

## <a name="methods-pane"></a>Volet Méthodes

<xref:System.Data.Linq.DataContext> méthodes qui mappent aux procédures stockées et aux fonctions sont affichées dans le volet de **méthodes** du **Concepteur O/R**. Le volet **Méthodes** est le volet situé le long du côté du volet **Entités** (l’aire de conception principale). Le volet **méthodes** répertorie toutes les méthodes de <xref:System.Data.Linq.DataContext> que vous avez créées à l’aide du **Concepteur O/R**. Par défaut, le volet de **méthodes** est vide. Faites glisser des procédures stockées ou des fonctions de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R** pour créer <xref:System.Data.Linq.DataContext> méthodes et remplir le volet de **méthodes** . Pour plus d’informations, consultez [Comment : créer des méthodes DataContext mappées à des procédures stockées et des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Ouvrez et fermez le volet méthodes en cliquant avec le bouton droit sur le **Concepteur O/R** , puis en cliquant sur **masquer le volet méthodes** ou **afficher le volet méthodes**, ou utilisez le raccourci clavier **CTRL** +**1**.

## <a name="two-types-of-datacontext-methods"></a>Deux types de méthodes DataContext

Les méthodes DataContext sont les méthodes qui mappent aux procédures stockées et aux fonctions dans la base de données. Vous pouvez créer et ajouter des méthodes DataContext dans le volet **méthodes** du **Concepteur O/R**. Il existe deux types distincts de méthodes <xref:System.Data.Linq.DataContext> : celles qui retournent un ou plusieurs jeux de résultats et celles qui ne retournent aucun jeu de résultats :

- Méthodes <xref:System.Data.Linq.DataContext> qui retournent un ou plusieurs jeux de résultats :

   Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit juste exécuter des procédures stockées et des fonctions dans la base de données et retourner les résultats. Pour plus d’informations, consultez [Comment : créer des méthodes DataContext mappées à des procédures stockées et des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. Linq. ISingleResult \<T > et <xref:System.Data.Linq.IMultipleResults>.

- Méthodes <xref:System.Data.Linq.DataContext> qui ne retournent aucun jeu de résultats, par exemple celles qui effectuent des insertions, des mises à jour et des suppressions pour une classe d'entité spécifique.

   Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit exécuter des procédures stockées au lieu d’utiliser le comportement [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] par défaut pour enregistrer des données modifiées entre une classe d’entité et la base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Types de retour des méthodes DataContext

Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R**, le type de retour de la méthode <xref:System.Data.Linq.DataContext> générée diffère selon l’endroit où vous déposez l’élément. La suppression des éléments directement dans une classe d’entité existante crée une <xref:System.Data.Linq.DataContext> méthode avec le type de retour de la classe d’entité ; la suppression d’éléments dans une zone vide du **Concepteur O/R** (dans l’un ou l’autre volet) crée une <xref:System.Data.Linq.DataContext> méthode qui retourne un type généré automatiquement. Le type généré automatiquement porte le nom qui correspond au nom de la procédure stockée ou de la fonction et aux propriétés, qui mappent aux champs retournés par la procédure stockée ou la fonction.

> [!NOTE]
> Vous pouvez modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext> après l’avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Les objets que vous faites glisser depuis la base de données sur l’aire du Concepteur O/R sont nommés automatiquement, en fonction du nom des objets dans la base de données. Si vous faites glisser plusieurs fois le même objet, un nombre est ajouté à la fin du nouveau nom qui différencie les noms. Lorsque les noms des objets de la base de données contiennent des espaces ou des caractères non pris en charge en Visual Basic ou en C#, l'espace ou le caractère non valide est remplacé par un trait de soulignement.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procédures stockées](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procédure pas à pas : Création de classes LINQ to SQL (Concepteur O/R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)