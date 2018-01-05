---
title: "Créer et configurer des groupes de données dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: da81d141e453e0106d329565338f7893b4fad758
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Créer et configurer des groupes de données dans Visual Studio

A *dataset* est un ensemble d’objets de stocker les données d’une base de données en mémoire et prend en charge le suivi des modifications pour activer la créer, lire, mettre à jour et supprimer (CRUD) des opérations sur ces données sans avoir à être toujours connectées à la base de données. Jeux de données ont été conçus pour simple *formulaires de données* applications d’entreprise. Pour les nouvelles applications, envisagez d’utiliser Entity Framework pour stocker et de modèle de données en mémoire. Pour utiliser des jeux de données, vous aurez une connaissance élémentaire des concepts de base de données.

Vous créez un typé <xref:System.Data.DataSet> classe dans Visual Studio au moment du design à l’aide de la **Assistant de Configuration de Source de données**. Pour plus d’informations sur la création de jeux de données par programme, consultez [création d’un jeu de données (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Créer un nouveau jeu de données à l’aide de l’Assistant Configuration de Source de données

1.  Sur le **projet** menu, cliquez sur **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.

2.  Choisissez le type de source de données que vous vous connecterez à.

     ![Assistant Configuration de Source de données](../data-tools/media/data-source-configuration-wizard.png "Assistant Configuration de Source de données")

3.  Pour les bases de données, choisissez la base de données ou les bases de données qui seront la source de données pour votre jeu de données.

     ![Source de données choisir une connexion](../data-tools/media/data-source-choose-a-connection.png "source de données choisir une connexion")

4.  Choisissez les tables (ou des colonnes individuelles), procédures stockées, fonctions et vues à partir de la base de données que vous souhaitez être représenté dans le jeu de données.

     ![Sélectionnez les objets de base de données](../data-tools/media/raddata-chose-objects.png "raddata choisi objets")

5.  Cliquez sur **Terminer**.

6.  Le jeu de données apparaît sous la forme d’un nœud dans **l’Explorateur de solutions**:

     ![Jeu de données dans l’Explorateur de solutions](../data-tools/media/dataset-in-solution-explorer.png "jeu de données dans l’Explorateur de solutions")

     Cliquez sur ce nœud, et le jeu de données apparaît dans le **Concepteur de DataSet**. Notez qu’un objet TableAdapter associé, qui est représenté en bas de chaque table dans le jeu de données. L’adaptateur de table est utilisé pour remplir le groupe et, éventuellement, pour envoyer des commandes à la base de données.

     ![Concepteur de DataSet](../data-tools/media/dataset-designer.png "Concepteur de DataSet")

7.  Les lignes de relation qui relient les tables représentent les relations entre les tables, tel que défini dans la base de données. Par défaut, les contraintes de clé étrangère dans une base de données sont représentées sous la forme d’une relation, la mise à jour et supprimer les règles de la valeur none. En règle générale, c’est ce que vous souhaitez. Toutefois, vous pouvez cliquer sur les lignes pour afficher les **Relation** boîte de dialogue, dans laquelle vous pouvez modifier le comportement des mises à jour hiérarchiques. Pour plus d’informations, consultez [des relations dans les jeux de données](../data-tools/relationships-in-datasets.md) et [mise à jour hiérarchique](../data-tools/hierarchical-update.md).

     ![Boîte de dialogue Relation de DataSet](../data-tools/media/raddata-relation-dialog.png "boîte de dialogue Relation raddata")

8.  Cliquez sur une table, l’adaptateur de table ou le nom de colonne dans une table pour afficher ses propriétés dans le **propriétés** fenêtre. Vous pouvez modifier certaines des valeurs ici. N’oubliez pas que vous modifiez le jeu de données, pas à la base de données source.

     ![Propriétés des colonnes de jeu de données](../data-tools/media/dataset-column-properties.png "propriétés des colonnes de jeu de données")

9. Vous pouvez ajouter de nouvelles tables ou les adaptateurs de table pour le jeu de données, ou ajouter de nouvelles requêtes pour les adaptateurs de table existant ou spécifier des relations entre les tables en faisant glisser les éléments à partir de la **boîte à outils** onglet. Cet onglet s’affiche lorsque le **Concepteur de DataSet** situé dans le focus.

     ![Boîte à outils DataSet](../data-tools/media/raddata-dataset-toolbox.png "raddata boîte à outils du jeu de données")

10. Ensuite, vous souhaiterez probablement spécifier comment remplir le dataset avec des données. Pour ce faire, vous utilisez la **Assistant Configuration de TableAdapter**. Pour plus d’informations, consultez [remplir des jeux de données à l’aide des TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Ajouter une table de base de données ou un autre objet à un dataset existant

Cette procédure montre comment ajouter une table à partir de la même base de données que vous avez utilisé d’abord créer le jeu de données.

1.  Cliquez sur le nœud de dataset dans **l’Explorateur de solutions** pour placer le focus sur le Concepteur de dataset.

2.  Cliquez sur le **des Sources de données** onglet dans la marge gauche de Visual Studio, ou entrez `Data Sources` dans **lancement rapide**.

3.  Cliquez sur le nœud de dataset et sélectionnez **configurer la Source de données avec l’Assistant**.

     ![Menu de contexte de Source de données](../data-tools/media/data-source-context-menu.png "menu contextuel de Source de données")

4.  Utilisez l’Assistant pour spécifier les tables supplémentaires, ou des procédures stockées ou autre objet de base de données, à ajouter au jeu de données.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Ajouter une table de données autonome à un jeu de données

1.  Ouvrez votre dataset dans le **Concepteur de Dataset**.

2.  Faites glisser un <xref:System.Data.DataTable> classe à partir de la **DataSet** onglet de la **boîte à outils** sur la **Concepteur de Dataset**.

3.  Ajouter des colonnes pour définir votre table de données. Avec le bouton droit sur la table et choisissez **Ajouter > colonne**. Utilisez le **propriétés** fenêtre pour définir le type de données de la colonne et une clé si nécessaire.

4.  Les tables autonomes doivent implémenter `Fill` logique dans les tables autonomes afin que vous pouvez les remplir de données. Pour plus d’informations sur le remplissage des tables de données autonomes, consultez [remplissage d’un DataSet à partir d’un DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Voir aussi

[Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)