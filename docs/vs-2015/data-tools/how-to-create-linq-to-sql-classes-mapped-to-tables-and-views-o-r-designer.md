---
title: 'Procédure : Créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5b6e661a79f190e5befdbcf5c28ec0f4bd29ebf4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061578"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procédure : créer des classes LINQ to SQL mappées à des tables et à des vues (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Classes LINQ to SQL qui sont mappées aux tables de base de données et les vues sont appelées *classes d’entité*. La classe d'entité mappe à un enregistrement, alors que les propriétés individuelles d'une classe d'entité mappent aux colonnes individuelles qui composent un enregistrement. Créer des classes d’entité qui sont basées sur les tables de base de données ou des vues en faisant glisser des tables ou des vues de **Explorateur de serveurs**/**Database Explorer** sur la [outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] génère les classes et applique les spécifiques [ ! LINQ aux attributs SQL pour activer [ ! LINQ aux fonctionnalités SQL (la communication de données et la modification des fonctionnalités de la <xref:System.Data.Linq.DataContext>). Pour plus d’informations sur [ ! Classes LINQ to SQL, consultez [le modèle LINQ to SQL objet](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> Le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] est un mappeur relationnel objet simple, car il prend en charge uniquement les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d'une classe d'entité à plusieurs tables, n'est pas pris en charge. Toutefois, vous pouvez mapper une classe d'entité à une vue qui joint plusieurs tables associées.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Création de classes LINQ to SQL mappées à des tables ou vues de base de données
 En faisant glisser des tables ou vues à partir de **Explorateur de serveurs**/**l’Explorateur de base de données** sur le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crée des classes d’entité en plus de la <xref:System.Data.Linq.DataContext> méthodes qui sont utilisées pour effectue des mises à jour.

 Par défaut, le [ ! Exécution LINQ to SQL crée la logique pour enregistrer les modifications à partir d’une classe d’entité d’être mise à jour dans la base de données. Cette logique est basée sur le schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas ce comportement, vous pouvez configurer une classe d’entité pour utiliser des procédures stockées pour effectuer des insertions, mises à jour et les supprime au lieu d’utiliser la valeur par défaut [ ! LINQ au comportement d’exécution SQL. Pour plus d'informations, voir [Procédure : affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Pour créer des classes LINQ to SQL mappées à des tables ou vues de base de données

1. Dans **Server**/**Database Explorer**, développez **Tables** ou **vues** et localisez la table de base de données ou afficher ou que vous souhaitez à utiliser dans votre application.

2. Faites glisser la table ou la vue vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d'entité a des propriétés qui mappent aux colonnes de la table ou de la vue sélectionnée.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Création d'un objet source de données et affichage des données sur un formulaire
 Après avoir créé des classes d’entité à l’aide de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], vous pouvez créer un objet source de données et remplir la [fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) avec les classes d’entité.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Pour créer un objet source de données basé sur des classes d'entité LINQ to SQL

1. Dans le menu **Générer**, cliquez sur **Générer la solution** pour générer votre projet.

2. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

4. Dans la page **Choisir un type de source de données**, cliquez sur **Objet**, puis sur **Suivant**.

5. Développez les nœuds, puis localisez et sélectionnez votre classe.

    > [!NOTE]
    > Si la classe **Customer** n’est pas disponible, quittez l’Assistant, générez le projet et réexécutez l’Assistant.

6. Cliquez sur **Terminer** pour créer la source de données et ajouter la classe d’entité **Customer** à la fenêtre **Sources de données**.

7. Faites glisser les éléments de la fenêtre **Sources de données** sur le formulaire.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext, méthodes (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modèle objet LINQ to SQL](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Procédure pas à pas : Personnaliser l’insertion, mettre à jour et supprimer le comportement de classes d’entités](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procédure pas à pas : Ajout d’une Validation aux Classes d’entité](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Guide pratique pour créer une association (relation) entre des classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)