---
title: Mapper des classes LINQ to SQL à des tables/vues (Concepteur O-R)
description: Comprendre comment créer des classes d’entité LINQ to SQL (classes mappées à des tables et des vues) dans Concepteur Objet Relationnel (Concepteur O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 79e5c529c1aefb4777e174489fc8fd1ca95a4111
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436344"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Guide pratique pour créer des classes LINQ to SQL mappées à des tables et à des vues (Concepteur O/R)

Les classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] mappées à des tables de base de données et à des vues sont appelées *classes d’entité*. La classe d'entité mappe à un enregistrement, alors que les propriétés individuelles d'une classe d'entité mappent aux colonnes individuelles qui composent un enregistrement. Créez des classes d’entité basées sur des tables ou des vues de base de données en faisant glisser des tables ou des vues à partir de **Explorateur de serveurs** ou **Explorateur de base de données** vers les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Le **Concepteur O/R** génère les classes et applique les [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] attributs spécifiques pour activer les [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] fonctionnalités (fonctionnalités de communication et de modification des données du <xref:System.Data.Linq.DataContext> ). Pour plus d’informations sur [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] les classes, consultez [le modèle objet LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> Le **Concepteur O/R** est un mappeur relationnel objet simple, car il ne prend en charge que les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d'une classe d'entité à plusieurs tables, n'est pas pris en charge. Toutefois, vous pouvez mapper une classe d'entité à une vue qui joint plusieurs tables associées.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Créer des classes LINQ to SQL mappées à des tables ou des vues de base de données

Le fait de faire glisser des tables ou des vues à partir de **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur O/R** crée des classes d’entité en plus des <xref:System.Data.Linq.DataContext> méthodes utilisées pour effectuer des mises à jour.

Par défaut, le runtime de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crée la logique pour enregistrer dans la base de données les modifications apportées à une classe d'entité qui peut être mise à jour. Cette logique est basée sur le schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas ce comportement, vous pouvez configurer une classe d’entité pour utiliser des procédures stockées afin d’effectuer des insertions, des mises à jour et des suppressions au lieu d’utiliser le comportement par défaut au moment de l' [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] exécution. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Pour créer des classes LINQ to SQL mappées à des tables ou vues de base de données

1. Dans l’ **Explorateur de serveurs** ou l’ **Explorateur de base de données** , développez **Tables** ou **Vues** , et localisez la table ou la vue de base de données que vous voulez utiliser dans votre application.

2. Faites glisser la table ou la vue dans le **Concepteur O/R**.

     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d'entité a des propriétés qui mappent aux colonnes de la table ou de la vue sélectionnée.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Créer un objet source de données et afficher les données sur un formulaire

Après avoir créé des classes d’entité à l’aide du **Concepteur O/R** , vous pouvez créer une source de données d’objet et remplir la [fenêtre sources de données](add-new-data-sources.md#data-sources-window) avec les classes d’entité.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Pour créer un objet source de données basé sur des classes d'entité LINQ to SQL

1. Dans le menu **Générer** , cliquez sur **Générer la solution** pour générer votre projet.

2. Pour ouvrir la fenêtre **sources de données** , dans le menu **données** , cliquez sur Afficher les **sources de données**.

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

4. Dans la page **Choisir un type de source de données** , cliquez sur **Objet** , puis sur **Suivant**.

5. Développez les nœuds, puis localisez et sélectionnez votre classe.

    > [!NOTE]
    > Si la classe **Customer** n’est pas disponible, quittez l’Assistant, générez le projet et réexécutez l’Assistant.

6. Cliquez sur **Terminer** pour créer la source de données et ajouter la classe d’entité **Customer** à la fenêtre **Sources de données**.

7. Faites glisser les éléments de la fenêtre **Sources de données** sur le formulaire.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création de classes LINQ to SQL (Concepteur O/R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Méthode DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modèle objet LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Guide pratique pour créer une association (relation) entre des classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
