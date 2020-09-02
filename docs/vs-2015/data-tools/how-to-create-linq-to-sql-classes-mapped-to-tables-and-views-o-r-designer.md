---
title: 'Comment : créer des classes LINQ to SQL mappées à des tables et des vues (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665928"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Guide pratique pour créer des classes LINQ to SQL mappées à des tables et à des vues (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL classes mappées à des tables et des vues de base de données sont appelées *classes d’entité*. La classe d'entité mappe à un enregistrement, alors que les propriétés individuelles d'une classe d'entité mappent aux colonnes individuelles qui composent un enregistrement. Créez des classes d’entité basées sur des tables ou des vues de base de données en faisant glisser des tables ou des vues à partir de **Explorateur de serveurs** / **Explorateur de base de données** vers les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Génère les classes et applique les [ ! LINQ to SQL attributs pour activer [ ! LINQ to SQL fonctionnalités (fonctionnalités de communication et de modification des données de <xref:System.Data.Linq.DataContext> ). Pour plus d’informations sur [ ! LINQ to SQL les classes, consultez [le modèle objet LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Est un mappeur relationnel objet simple, car il ne prend en charge que les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d'une classe d'entité à plusieurs tables, n'est pas pris en charge. Toutefois, vous pouvez mapper une classe d'entité à une vue qui joint plusieurs tables associées.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Création de classes LINQ to SQL mappées à des tables ou vues de base de données
 Le fait de faire glisser des tables ou des vues à partir de **Explorateur de serveurs** / **Explorateur de base de données** vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crée des classes d’entité en plus des <xref:System.Data.Linq.DataContext> méthodes utilisées pour effectuer des mises à jour.

 Par défaut, les [ ! LINQ to SQL Runtime crée une logique pour enregistrer les modifications apportées à une classe d’entité pouvant être mise à jour dans la base de données. Cette logique est basée sur le schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas ce comportement, vous pouvez configurer une classe d’entité pour utiliser des procédures stockées afin d’effectuer des insertions, des mises à jour et des suppressions au lieu d’utiliser la valeur par défaut [ ! LINQ to SQL comportement d’exécution. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Pour créer des classes LINQ to SQL mappées à des tables ou vues de base de données

1. Dans **Server** / **Explorateur de base de données**de serveur, développez **tables** ou **vues** et localisez la table ou la vue de base de données que vous souhaitez utiliser dans votre application.

2. Faites glisser la table ou la vue vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d'entité a des propriétés qui mappent aux colonnes de la table ou de la vue sélectionnée.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Création d'un objet source de données et affichage des données sur un formulaire
 Après avoir créé des classes d’entité à l’aide de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , vous pouvez créer une source de données d’objet et remplir la [fenêtre sources de données](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) avec les classes d’entité.

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

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procédure pas à pas : création de classes LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Méthode DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Guide pratique pour créer des méthodes DataContext mappées à des procédures stockées et à des fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modèle objet LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procédure pas à pas : ajout d’une validation à des classes d’entité](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Guide pratique pour créer une association (relation) entre des classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)