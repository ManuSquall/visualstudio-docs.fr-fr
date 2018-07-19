---
title: 'Comment : créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089323"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Comment : créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O/R)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] les classes qui sont mappées aux tables de base de données et les vues sont appelées *classes d’entité*. La classe d'entité mappe à un enregistrement, alors que les propriétés individuelles d'une classe d'entité mappent aux colonnes individuelles qui composent un enregistrement. Créer des classes d’entité qui sont basées sur les tables de base de données ou des vues en faisant glisser des tables ou des vues de **Explorateur de serveurs** ou **Database Explorer** sur la [des outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Le **Concepteur O/R** génère les classes et applique les spécifiques [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] attributs pour activer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] fonctionnalité (la communication de données et la modification des fonctionnalités de la <xref:System.Data.Linq.DataContext>). Pour plus d’informations sur [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] des classes, consultez [le modèle LINQ to SQL objet](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  Le **Concepteur O/R** est un mappeur relationnel objet simple, car il prend en charge uniquement les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d'une classe d'entité à plusieurs tables, n'est pas pris en charge. Toutefois, vous pouvez mapper une classe d'entité à une vue qui joint plusieurs tables associées.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Créer des LINQ to SQL des classes qui sont mappées aux tables de base de données ou des vues
 En faisant glisser des tables ou vues à partir de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R** crée des classes d’entité en plus de la <xref:System.Data.Linq.DataContext> méthodes qui sont utilisées pour effectuer des mises à jour.

 Par défaut, le runtime de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crée la logique pour enregistrer dans la base de données les modifications apportées à une classe d'entité qui peut être mise à jour. Cette logique est basée sur le schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas ce comportement, vous pouvez configurer une classe d’entité pour utiliser des procédures stockées pour effectuer des insertions, mises à jour et suppressions au lieu d’utiliser la valeur par défaut [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportement d’exécution. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Pour créer des classes LINQ to SQL mappées à des tables ou vues de base de données

1.  Dans **Server** ou **Database Explorer**, développez **Tables** ou **vues** et localisez la table de base de données ou afficher ou que vous souhaitez utiliser dans votre application.

2.  Faites glisser la table ou la vue vers le **Concepteur O/R**.

     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d'entité a des propriétés qui mappent aux colonnes de la table ou de la vue sélectionnée.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Créer un objet source de données et afficher les données sur un formulaire
 Après avoir créé des classes d’entité à l’aide de la **Concepteur O/R**, vous pouvez créer un objet source de données et remplir la [fenêtre Sources de données](add-new-data-sources.md) avec les classes d’entité.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Pour créer un objet source de données basé sur des classes d'entité LINQ to SQL

1.  Sur le **Build** menu, cliquez sur **générer la Solution** pour générer votre projet.

2.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

3.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

4.  Cliquez sur **objet** sur le **choisir un Type de Source de données** page, puis cliquez sur **suivant**.

5.  Développez les nœuds, puis localisez et sélectionnez votre classe.

    > [!NOTE]
    >  Si le **client** classe n’est pas disponible, quittez l’Assistant, générez le projet, et réexécutez l’Assistant.

6.  Cliquez sur **Terminer** pour créer la source de données et ajouter la **client** classe d’entité à la **des Sources de données** fenêtre.

7.  Faites glisser des éléments à partir de la **des Sources de données** fenêtre vers un formulaire.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de LINQ to SQL classes (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Le modèle LINQ to SQL objet](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)