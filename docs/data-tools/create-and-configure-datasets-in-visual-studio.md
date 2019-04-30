---
title: Créer et configurer des datasets
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b71d4b8ea58cbbe36e3fe48228789d4aee02af53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567732"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Créer et configurer des datasets dans Visual Studio

Un jeu de données est un ensemble d’objets de stocker des données à partir d’une base de données en mémoire et prend en charge le suivi des modifications pour activer la créer, lire, mettre à jour et supprimer (CRUD) des opérations sur ces données sans avoir à être toujours connectés à la base de données. Jeux de données ont été conçus pour simple *formulaires sur données* applications métier. Pour les nouvelles applications, envisagez d’utiliser Entity Framework pour stocker et modéliser des données en mémoire. Pour utiliser des jeux de données, vous devez posséder une connaissance base des concepts de base de données.

Vous pouvez créer un typé <xref:System.Data.DataSet> classe dans Visual Studio au moment du design à l’aide de la **Assistant de Configuration de Source de données**. Pour plus d’informations sur la création de jeux de données par programmation, consultez [création d’un dataset (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Créer un nouveau jeu de données à l’aide de l’Assistant de Configuration de Source de données

1. Ouvrez votre projet dans Visual Studio, puis choisissez **projet** > **ajouter une nouvelle Source de données** pour démarrer le **Assistant de Configuration de Source de données**.

2. Choisissez le type de source de données auquel vous vous connecterez.

     ![Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png)

3. Choisissez la base de données ou les bases de données qui seront la source de données pour votre jeu de données.

     ![Source de données choisir une connexion](../data-tools/media/data-source-choose-a-connection.png)

4. Choisissez les tables (ou des colonnes individuelles), procédures stockées, fonctions et vues à partir de la base de données que vous souhaitez être représenté dans le jeu de données.

     ![Choisir des objets de base de données](../data-tools/media/raddata-chose-objects.png)

5. Cliquez sur **Terminer**.

   Le jeu de données apparaît sous la forme d’un nœud dans **l’Explorateur de solutions**.

   ![Jeu de données dans l’Explorateur de solutions](../data-tools/media/dataset-in-solution-explorer.png)

6. Cliquez sur le nœud de jeu de données dans **l’Explorateur de solutions** pour ouvrir le jeu de données dans le **Concepteur de DataSet**. Chaque table dans le jeu de données est associé à un `TableAdapter` objet, qui est représenté en bas. L’adaptateur de table est utilisé pour remplir le jeu de données et éventuellement pour envoyer des commandes à la base de données.

   ![Concepteur de DataSet](../data-tools/media/dataset-designer.png)

7. Les lignes de relation qui relient les tables représentent les relations entre les tables, tel que défini dans la base de données. Par défaut, les contraintes de clé étrangère dans une base de données sont représentées sous la forme d’une relation uniquement, la mise à jour et supprimer des règles la valeur none. En règle générale, c’est ce que vous souhaitez. Toutefois, vous pouvez cliquer sur les lignes pour afficher le **Relation** boîte de dialogue, où vous pouvez modifier le comportement des mises à jour hiérarchiques. Pour plus d’informations, consultez [relations dans les datasets](../data-tools/relationships-in-datasets.md) et [mise à jour hiérarchique](../data-tools/hierarchical-update.md).

     ![Boîte de dialogue Relation de DataSet](../data-tools/media/raddata-relation-dialog.png)

8. Cliquez sur une table, l’adaptateur de table ou le nom de colonne dans une table pour afficher ses propriétés dans le **propriétés** fenêtre. Vous pouvez modifier certaines valeurs ici. N’oubliez pas que vous modifiez le jeu de données, pas la base de données source.

     ![Propriétés des colonnes de jeu de données](../data-tools/media/dataset-column-properties.png)

9. Vous pouvez ajouter de nouvelles tables ou les adaptateurs de table pour le jeu de données, ou ajouter de nouvelles requêtes pour les adaptateurs de table existants ou spécifier des relations entre les tables en faisant glisser ces éléments à partir de la **boîte à outils** onglet. Cet onglet s’affiche lorsque le **Concepteur de DataSet** a le focus.

     ![Boîte à outils du jeu de données](../data-tools/media/raddata-dataset-toolbox.png)

Ensuite, vous souhaiterez peut-être spécifier comment remplir le dataset avec des données. Pour ce faire, vous utilisez le **Assistant Configuration de TableAdapter**. Pour plus d’informations, consultez [remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Ajouter une table de base de données ou un autre objet à un dataset existant

Cette procédure montre comment ajouter une table à partir de la même base de données que vous avez utilisé d’abord créer le jeu de données.

1. Cliquez sur le nœud de jeu de données dans **l’Explorateur de solutions** pour afficher le **Concepteur de DataSet** le focus.

2. Cliquez sur le **des Sources de données** onglet dans la marge gauche de Visual Studio, ou type **des sources de données** dans la zone de recherche.

3. Cliquez sur le nœud de jeu de données et sélectionnez **configurer la Source de données avec l’Assistant**.

     ![Menu de contexte de Source de données](../data-tools/media/data-source-context-menu.png)

4. Utilisez l’Assistant pour spécifier quelles tables supplémentaires, des procédures stockées ou des autres objets de base de données à ajouter au jeu de données.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Ajouter une table de données autonome à un jeu de données

1. Ouvrez votre dataset dans le **Concepteur de DataSet**.

2. Faites glisser un <xref:System.Data.DataTable> classe à partir de la **DataSet** onglet de la **boîte à outils** sur le **Concepteur de Dataset**.

3. Ajouter des colonnes pour définir votre table de données. Avec le bouton droit sur la table et choisissez **ajouter** > **colonne**. Utilisez le **propriétés** fenêtre pour définir le type de données de la colonne et une clé si nécessaire.

Les tables autonomes doivent implémenter `Fill` logique dans les tables autonomes afin que vous pouvez les remplir de données. Pour plus d’informations sur le remplissage des tables de données autonome, consultez [remplissage d’un DataSet à partir d’un DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relations dans les datasets](../data-tools/relationships-in-datasets.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)