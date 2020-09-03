---
title: Créer et configurer des datasets
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631205"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Créer et configurer des datasets dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *jeu de données est un* ensemble d’objets qui stockent des données à partir d’une base de données en mémoire et prennent en charge le suivi des modifications pour permettre des opérations de création, de lecture, de mise à jour et de suppression sur ces données sans qu’il soit nécessaire de toujours les connecter à la base de données. Les jeux de données ont été conçus pour des *formulaires simples sur* des applications métier de données. Pour les nouvelles applications, envisagez d’utiliser Entity Framework pour stocker et modéliser des données en mémoire. Pour travailler avec des jeux de données, vous devez avoir une connaissance de base des concepts de base de données.

 Vous créez une classe typée <xref:System.Data.DataSet> dans Visual Studio au moment du design à l’aide de l' **Assistant Configuration de source de données**. Pour plus d’informations sur la création de jeux de données par programme, consultez [création d’un DataSet](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Créer un nouveau DataSet à l’aide de l’Assistant Configuration de source de données

1. Dans le menu **projet** , cliquez sur **Ajouter une nouvelle source de données** pour démarrer l' **Assistant Configuration de source de données**.

2. Choisissez le type de source de données à laquelle vous allez vous connecter.

     ![Assistant Configuration de source de données](../data-tools/media/data-source-configuration-wizard.png "Assistant Configuration de source de données")

3. Pour les bases de données, choisissez la ou les bases de données qui seront la source de données de votre jeu de données.

     ![Source de données choisir une connexion](../data-tools/media/data-source-choose-a-connection.png "Source de données choisir une connexion")

4. Choisissez les tables (ou colonnes individuelles), les procédures stockées, les fonctions et les vues de la base de données que vous souhaitez représenter dans le DataSet.

     ![Choisir des objets de base de données](../data-tools/media/raddata-chose-objects.png "raddata a choisi objets")

5. Cliquez sur **Terminer**.

6. Le jeu de données apparaît sous la forme d’un nœud dans **Explorateur de solutions**:

     ![Jeu de données dans Explorateur de solutions](../data-tools/media/dataset-in-solution-explorer.png "Jeu de données dans Explorateur de solutions")

     Cliquez sur ce nœud pour afficher le jeu de données dans le **Concepteur de DataSet**. Notez que chaque table du DataSet est associée à un objet TableAdapter, qui est représenté en bas. L’adaptateur de table est utilisé pour remplir le DataSet et éventuellement pour envoyer des commandes à la base de données.

     ![Concepteur de DataSet](../data-tools/media/dataset-designer.png "Concepteur de DataSet")

7. Les lignes de relation qui connectent les tables représentent les relations entre les tables, comme défini dans la base de données. Par défaut, les contraintes de clé étrangère dans une base de données sont représentées en tant que relation uniquement, avec les règles de mise à jour et de suppression définies sur aucun. En général, c’est ce que vous voulez. Toutefois, vous pouvez cliquer sur les lignes pour afficher la boîte de dialogue **relation** , dans laquelle vous pouvez modifier le comportement des mises à jour hiérarchiques. Pour plus d’informations, consultez [relations dans les jeux de données](../data-tools/relationships-in-datasets.md) et [mise à jour hiérarchique](../data-tools/hierarchical-update.md).

     ![Boîte de dialogue relation de DataSet](../data-tools/media/raddata-relation-dialog.png "boîte de dialogue relation raddata")

8. Cliquez sur une table, un adaptateur de table ou un nom de colonne dans un tableau pour afficher ses propriétés dans la fenêtre **Propriétés** . Vous pouvez modifier certaines valeurs ici. Rappelez-vous simplement que vous modifiez le jeu de données, et non la base de données source.

     ![Propriétés des colonnes du DataSet](../data-tools/media/dataset-column-properties.png "Propriétés des colonnes du DataSet")

9. Vous pouvez ajouter de nouvelles tables ou adaptateurs de table au DataSet, ou ajouter de nouvelles requêtes pour les adaptateurs de table existants, ou spécifier de nouvelles relations entre des tables en faisant glisser ces éléments à partir de l’onglet **boîte à outils** . Cet onglet apparaît lorsque le **Concepteur de DataSet** est actif.

     ![Boîte à outils DataSet](../data-tools/media/raddata-dataset-toolbox.png "Boîte à outils du DataSet raddata")

10. Ensuite, vous souhaiterez probablement spécifier comment remplir le DataSet avec des données. Pour cela, vous utilisez l' **Assistant Configuration de TableAdapter**. Pour plus d’informations, consultez [remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Ajouter une table de base de données ou un autre objet à un DataSet existant
 Cette procédure montre comment ajouter une table à partir de la même base de données que celle que vous avez utilisée pour créer le jeu de données.

1. Cliquez sur le nœud du DataSet dans **Explorateur de solutions** pour activer le concepteur de DataSet.

2. Cliquez sur l’onglet **sources de données** dans la marge de gauche de Visual Studio, ou entrez `Data Sources` dans **QuickLaunch**.

3. Cliquez avec le bouton droit sur le nœud du DataSet, puis sélectionnez **configurer la source de données avec l’Assistant** .

     ![Menu contextuel de la source de données](../data-tools/media/data-source-context-menu.png "Menu contextuel de la source de données")

4. Utilisez l’Assistant pour spécifier les tables supplémentaires ou les procédures stockées ou un autre objet de base de données à ajouter au DataSet.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Ajouter une table de données autonome à un DataSet

1. Ouvrez votre dataset dans le **Concepteur de DataSet**.

2. Faites glisser une <xref:System.Data.DataTable> classe de l’onglet **DataSet** de la **boîte à outils** vers le **Concepteur de DataSet**.

3. Ajoutez des colonnes pour définir votre table de données. Pour plus d’informations, consultez [Comment : ajouter des colonnes à un DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Les tables autonomes doivent implémenter `Fill` une logique dans les tables autonomes afin que vous puissiez les remplir avec des données. Pour plus d’informations sur le remplissage de tables de données autonomes, consultez [remplissage d’un DataSet à partir d’un DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
