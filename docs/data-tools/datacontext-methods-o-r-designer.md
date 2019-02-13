---
title: DataContext, méthodes (Concepteur O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 83ca0059e576683571435764914bf0087eded2fa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951161"
---
# <a name="datacontext-methods-or-designer"></a>DataContext, méthodes (Concepteur O/R)

<xref:System.Data.Linq.DataContext> méthodes (dans le contexte de la [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sont des méthodes de la <xref:System.Data.Linq.DataContext> classe qui s’exécutent des procédures stockées et fonctions dans une base de données.

La classe <xref:System.Data.Linq.DataContext> est une classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] qui agit comme un conduit entre une base de données SQL Server et les classes d'entité [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] mappées à cette base de données. La classe <xref:System.Data.Linq.DataContext> contient les informations de chaîne de connexion et les méthodes pour se connecter à une base de données et manipuler les données dans celle-ci. Par défaut, la classe <xref:System.Data.Linq.DataContext> contient plusieurs méthodes que vous pouvez appeler, telles que la méthode <xref:System.Data.Linq.DataContext.SubmitChanges%2A> qui envoie des données mises à jour des classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] vers la base de données. Vous pouvez également créer des méthodes <xref:System.Data.Linq.DataContext> supplémentaires pour mapper aux procédures stockées et aux fonctions. En d’autres termes, l’appel de ces méthodes personnalisées s’exécute la procédure stockée ou une fonction dans la base de données à laquelle le <xref:System.Data.Linq.DataContext> méthode est mappée. Vous pouvez ajouter de nouvelles méthodes à la classe <xref:System.Data.Linq.DataContext> en procédant comme pour l'ajout de toute autre méthode destinée à étendre une classe. Toutefois, des discussions sur <xref:System.Data.Linq.DataContext> méthodes dans le contexte de la **Concepteur O/R**, il est le <xref:System.Data.Linq.DataContext> méthodes qui mappent aux procédures stockées et fonctions qui sont examinées.

## <a name="methods-pane"></a>Volet Méthodes

<xref:System.Data.Linq.DataContext> les méthodes qui mappent aux procédures stockées et fonctions sont affichées dans le **méthodes** volet de la **Concepteur O/R**. Le volet **Méthodes** est le volet situé le long du côté du volet **Entités** (l’aire de conception principale). Le **méthodes** volet répertorie tous les <xref:System.Data.Linq.DataContext> méthodes que vous avez créé à l’aide de la **Concepteur O/R**. Par défaut, le **méthodes** volet est vide ; faites glisser des procédures stockées ou fonctions de **Explorateur de serveurs** ou **Database Explorer** sur la **Concepteur O/R**  créer <xref:System.Data.Linq.DataContext> méthodes et remplir la **méthodes** volet. Pour plus d’informations, consultez [Comment : créer un DataContext, méthodes mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Ouvrir et fermer le volet de méthodes en double-cliquant sur le **Concepteur O/R** , puis en cliquant sur **masquer le volet méthodes** ou **afficher le volet méthodes**, ou utilisez le raccourci clavier  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Deux types de méthodes DataContext

Les méthodes DataContext sont les méthodes qui mappent aux procédures stockées et aux fonctions dans la base de données. Vous pouvez créer et ajouter des méthodes DataContext sur le **méthodes** volet de la **Concepteur O/R**. Il existe deux types distincts de méthodes <xref:System.Data.Linq.DataContext> : celles qui retournent un ou plusieurs jeux de résultats et celles qui ne retournent aucun jeu de résultats :

- Méthodes <xref:System.Data.Linq.DataContext> qui retournent un ou plusieurs jeux de résultats :

   Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit juste exécuter des procédures stockées et des fonctions dans la base de données et retourner les résultats. Pour plus d’informations, consultez [Comment : créer un DataContext, méthodes mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, et <xref:System.Data.Linq.IMultipleResults>.

- Méthodes <xref:System.Data.Linq.DataContext> qui ne retournent aucun jeu de résultats, par exemple celles qui effectuent des insertions, des mises à jour et des suppressions pour une classe d'entité spécifique.

   Créez ce type de méthode <xref:System.Data.Linq.DataContext> lorsque votre application doit exécuter des procédures stockées au lieu d’utiliser le comportement [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] par défaut pour enregistrer des données modifiées entre une classe d’entité et la base de données. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Types de retour des méthodes DataContext

Lorsque vous faites glisser des procédures stockées et des fonctions de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R**, le type de retour de généré <xref:System.Data.Linq.DataContext> méthode diffère selon l’endroit où vous placez l’élément. Suppression d’éléments directement sur une classe d’entité existante crée une <xref:System.Data.Linq.DataContext> méthode avec le type de retour de la classe d’entité ; placer des éléments dans une zone vide de la **Concepteur O/R** (dans le volet) crée un <xref:System.Data.Linq.DataContext> (méthode) qui retourne un type généré automatiquement. Le type généré automatiquement a le nom correspond à la procédure stockée ou de nom de la fonction et de propriétés qui correspondent aux champs retournés par la procédure stockée ou une fonction.

> [!NOTE]
> Vous pouvez modifier le type de retour d'une méthode <xref:System.Data.Linq.DataContext> après l'avoir ajoutée au volet de méthodes. Pour inspecter ou modifier le type de retour d’une méthode <xref:System.Data.Linq.DataContext>, sélectionnez-la et inspectez la propriété **Type de retour** dans la fenêtre **Propriétés**. Pour plus d’informations, consultez [Comment : modifier le type de retour d’une méthode DataContext (Concepteur O/R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Objets que vous faites glisser à partir de la base de données sur l’aire du Concepteur O/R sont nommés automatiquement, en fonction du nom des objets dans la base de données. Si vous faites glisser le même objet plusieurs fois, un numéro est ajouté à la fin du nouveau nom qui différencie les noms. Lorsque les noms des objets de la base de données contiennent des espaces ou des caractères non pris en charge en Visual Basic ou en C#, l'espace ou le caractère non valide est remplacé par un trait de soulignement.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procédures stockées](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procédure pas à pas : Création de classes LINQ to SQL (Concepteur O/R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)