---
title: Créer et configurer des datasets
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 44023543f1f7b57352448755de942af1c0c712ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642401"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Comment : créer et configurer des datasets dans Visual Studio

Un jeu de données est un ensemble d’objets qui stockent des données à partir d’une base de données en mémoire et prennent en charge le suivi des modifications pour permettre les opérations de création, lecture, mise à jour et suppression (CRUD) sur ces données sans qu’il soit nécessaire de toujours les connecter à la base de données. Les jeux de données ont été conçus pour des *formulaires simples sur* des applications métier de données. Pour les nouvelles applications, envisagez d’utiliser Entity Framework pour stocker et modéliser des données en mémoire. Pour travailler avec des jeux de données, vous devez avoir une connaissance de base des concepts de base de données.

Vous pouvez créer une classe de <xref:System.Data.DataSet> typée dans Visual Studio au moment du design à l’aide de l' **Assistant Configuration de source de données**. Pour plus d’informations sur la création de jeux de données par programme, consultez [création d’un jeu de données (ADO.net)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Créer un nouveau DataSet à l’aide de l’Assistant Configuration de source de données

1. Ouvrez votre projet dans Visual Studio, puis choisissez **projet**  > **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

2. Choisissez le type de source de données à laquelle vous souhaitez vous connecter.

     ![Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png)

3. Choisissez la ou les bases de données qui seront la source de données de votre jeu de données.

     ![Source de données choisir une connexion](../data-tools/media/data-source-choose-a-connection.png)

4. Choisissez les tables (ou colonnes individuelles), les procédures stockées, les fonctions et les vues de la base de données que vous souhaitez représenter dans le DataSet.

     ![Choisir des objets de base de données](../data-tools/media/raddata-chose-objects.png)

5. Cliquez sur **Finish**.

   Le jeu de données apparaît sous la forme d’un nœud dans **Explorateur de solutions**.

   ![Jeu de données dans Explorateur de solutions](../data-tools/media/dataset-in-solution-explorer.png)

6. Cliquez sur le nœud du DataSet dans **Explorateur de solutions** pour ouvrir le DataSet dans le **Concepteur de DataSet**. Chaque table du jeu de données est associée à un objet `TableAdapter`, qui est représenté en bas. L’adaptateur de table est utilisé pour remplir le DataSet et éventuellement pour envoyer des commandes à la base de données.

   ![Concepteur de DataSet](../data-tools/media/dataset-designer.png)

7. Les lignes de relation qui connectent les tables représentent les relations entre les tables, comme défini dans la base de données. Par défaut, les contraintes de clé étrangère dans une base de données sont représentées en tant que relation uniquement, avec les règles de mise à jour et de suppression définies sur aucun. En général, c’est ce que vous voulez. Toutefois, vous pouvez cliquer sur les lignes pour afficher la boîte de dialogue **relation** , dans laquelle vous pouvez modifier le comportement des mises à jour hiérarchiques. Pour plus d’informations, consultez [relations dans les jeux de données](../data-tools/relationships-in-datasets.md) et [mise à jour hiérarchique](../data-tools/hierarchical-update.md).

     ![Boîte de dialogue relation de DataSet](../data-tools/media/raddata-relation-dialog.png)

8. Cliquez sur une table, un adaptateur de table ou un nom de colonne dans un tableau pour afficher ses propriétés dans la fenêtre **Propriétés** . Vous pouvez modifier certaines valeurs ici. Rappelez-vous simplement que vous modifiez le jeu de données, et non la base de données source.

     ![Propriétés des colonnes du DataSet](../data-tools/media/dataset-column-properties.png)

9. Vous pouvez ajouter de nouvelles tables ou adaptateurs de table au DataSet, ou ajouter de nouvelles requêtes pour les adaptateurs de table existants, ou spécifier de nouvelles relations entre des tables en faisant glisser ces éléments à partir de l’onglet **boîte à outils** . Cet onglet apparaît lorsque le **Concepteur de DataSet** est actif.

     ![Boîte à outils DataSet](../data-tools/media/raddata-dataset-toolbox.png)

Ensuite, vous souhaiterez peut-être spécifier comment remplir le DataSet avec des données. Pour cela, vous utilisez l' **Assistant Configuration de TableAdapter**. Pour plus d’informations, consultez [remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Ajouter une table de base de données ou un autre objet à un DataSet existant

Cette procédure montre comment ajouter une table à partir de la même base de données que celle que vous avez utilisée pour créer le jeu de données.

1. Cliquez sur le nœud du DataSet dans **Explorateur de solutions** pour activer le **Concepteur de DataSet** .

2. Cliquez sur l’onglet **sources de données** dans la marge de gauche de Visual Studio, ou tapez **sources de données** dans la zone de recherche.

3. Cliquez avec le bouton droit sur le nœud du DataSet, puis sélectionnez **configurer la source de données avec l’Assistant**.

     ![Menu contextuel de la source de données](../data-tools/media/data-source-context-menu.png)

4. Utilisez l’Assistant pour spécifier les tables, les procédures stockées ou d’autres objets de base de données supplémentaires à ajouter au DataSet.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Ajouter une table de données autonome à un DataSet

1. Ouvrez votre dataset dans le **Concepteur de DataSet**.

2. Faites glisser une classe <xref:System.Data.DataTable> de l’onglet **DataSet** de la **boîte à outils** vers le **Concepteur de DataSet**.

3. Ajoutez des colonnes pour définir votre table de données. Cliquez avec le bouton droit sur la table et choisissez **ajouter**  > **colonne**. Utilisez la fenêtre **Propriétés** pour définir le type de données de la colonne et une clé si nécessaire.

Les tables autonomes doivent implémenter `Fill` logique dans les tables autonomes afin que vous puissiez les remplir avec des données. Pour plus d’informations sur le remplissage de tables de données autonomes, consultez [remplissage d’un DataSet à partir d’un DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relations dans les datasets](../data-tools/relationships-in-datasets.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)