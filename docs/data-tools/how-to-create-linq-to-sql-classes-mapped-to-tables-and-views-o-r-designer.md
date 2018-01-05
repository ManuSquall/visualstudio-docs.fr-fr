---
title: "Comment : créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O-R) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 3d295cc9527aae2f566f5ec4d1ba92a2b129fbd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Comment : créer des LINQ to SQL classes mappées aux tables et vues (Concepteur O/R)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]les classes qui sont mappées aux tables de base de données et les vues sont appelées *des classes d’entité*. La classe d'entité mappe à un enregistrement, alors que les propriétés individuelles d'une classe d'entité mappent aux colonnes individuelles qui composent un enregistrement. Créer des classes d’entité qui sont basées sur les tables de base de données ou des vues en faisant glisser des tables ou des vues de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [LINQ to SQL Tools dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] génère les classes et applique la spécifique [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] attributs pour activer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] fonctionnalité (la communication de données et modification de la <xref:System.Data.Linq.DataContext>). Pour plus d’informations sur les [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] des classes, consultez [le modèle LINQ to SQL objet](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).  
  
> [!NOTE]
>  Le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] est un mappeur relationnel objet simple, car il prend en charge que les relations de mappage 1:1. En d'autres termes, une classe d'entité peut uniquement avoir une relation de mappage 1:1 avec une table ou une vue de base de données. Le mappage complexe, tel que le mappage d'une classe d'entité à plusieurs tables, n'est pas pris en charge. Toutefois, vous pouvez mapper une classe d'entité à une vue qui joint plusieurs tables associées.  
  
## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Création de classes LINQ to SQL mappées à des tables ou vues de base de données  
 En faisant glisser des tables ou vues à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crée des classes d’entité à la <xref:System.Data.Linq.DataContext> les méthodes qui sont utilisés pour mise à jour.  
  
 Par défaut, le runtime de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crée la logique pour enregistrer dans la base de données les modifications apportées à une classe d'entité qui peut être mise à jour. Cette logique est basée sur le schéma de la table (les définitions de colonne et les informations de clé primaire). Si vous ne souhaitez pas ce comportement, vous pouvez configurer une classe d'entité pour utiliser des procédures stockées afin d'effectuer les insertions, les mises à jour et les suppressions au lieu d'utiliser le comportement au moment de l'exécution par défaut de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Pour plus d’informations, consultez [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Pour créer des classes LINQ to SQL mappées à des tables ou vues de base de données  
  
1.  Dans **Server**/**l’Explorateur de base de données**, développez **Tables** ou **vues** et localisez la table de base de données ou la vue que vous souhaitez à utiliser dans votre application.  
  
2.  Faites glisser la table ou la vue vers le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Une classe d'entité est créée et apparaît dans l'aire de conception. La classe d'entité a des propriétés qui mappent aux colonnes de la table ou de la vue sélectionnée.  
  
## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Création d'un objet source de données et affichage des données sur un formulaire  
 Après avoir créé des classes d’entité à l’aide de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vous pouvez créer un objet source de données et remplir les [fenêtre Sources de données](add-new-data-sources.md) avec les classes d’entité.  
  
#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Pour créer un objet source de données basé sur des classes d'entité LINQ to SQL  
  
1.  Sur le **générer** menu, cliquez sur **générer la Solution** pour générer votre projet.  
  
2.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
3.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
4.  Cliquez sur **objet** sur la **choisir un Type de Source de données** page, puis cliquez sur **suivant**.  
  
5.  Développez les nœuds, puis localisez et sélectionnez votre classe.  
  
    > [!NOTE]
    >  Si le **client** classe n’est pas disponible, quittez l’Assistant, générez le projet, et réexécutez l’Assistant.  
  
6.  Cliquez sur **Terminer** pour créer la source de données et ajouter la **client** classe d’entité à la **des Sources de données** fenêtre.  
  
7.  Faites glisser des éléments à partir de la **des Sources de données** fenêtre dans un formulaire.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procédure pas à pas : Création des Classes LINQ to SQL (Concepteur O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Méthodes DataContext (Concepteur O/R)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Comment : créer des méthodes DataContext mappées aux procédures stockées et fonctions (Concepteur O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Le modèle LINQ to SQL objet](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)   
 [Procédure pas à pas : Personnalisation de l’instruction insert, update et supprimez le comportement des classes d’entité](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
  [Comment : créer une association (relation) entre les classes LINQ to SQL (Concepteur O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)