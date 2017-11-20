---
title: Outils de DataSet dans Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6a7e5741b11263ef3c3730ddaa69e566cd7c2e24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Outils de DataSet dans Visual Studio
> [!NOTE]
>  Jeux de données et les classes associées sont des technologies .NET hérités à partir du début des années 2000 qui permettent aux applications de travailler avec des données en mémoire pendant que les applications sont déconnectées de la base de données. Ils sont particulièrement utiles pour les applications qui permettent aux utilisateurs de modifier des données et de conserver les modifications apportées à la base de données. Bien que les jeux de données s’est prouvées une technologie très réussie, nous recommandons d’utilisent Entity Framework nouvelles applications .NET. Entity Framework fournit un moyen plus naturel de travailler avec des données sous forme de tableau en tant que modèles d’objet, et il a une interface de programmation plus simple.  
  
 Un objet de jeu de données est un objet en mémoire qui est essentiellement un mini-de base de données. Il contient des objets DataRow, DataTable et DataColumn dans lequel vous pouvez stocker et modifier des données à partir d’une ou plusieurs bases de données sans avoir à maintenir une connexion ouverte. Le jeu de données gère les informations sur les modifications apportées à ses données, pour que les mises à jour peuvent être suivies et renvoyées à la base de données lorsque votre application est reconnectée.  
  
 Jeux de données et les classes associées sont définies dans l’espace de noms System.Data dans la bibliothèque de classes .NET Framework. Vous pouvez créer et modifier des jeux de données dynamiquement dans le code. Pour plus d’informations sur la procédure à suivre, consultez ADO.NET. La documentation de cette section montre comment utiliser des jeux de données à l’aide de concepteurs Visual Studio. Une chose à savoir : jeux de données qui est exécutées par les concepteurs utiliser objets TableAdapter pour interagir avec la base de données, tandis que les jeux de données qui est effectuées par programme utilisent des objets DataAdapter. Pour plus d’informations sur la création de jeux de données par programme, consultez [DataAdapters et DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Si votre application doit uniquement lire les données à partir d’une base de données et n’effectue pas les mises à jour, ajoute ou supprime, vous pouvez généralement obtenir de meilleures performances à l’aide d’un objet DataReader pour récupérer des données dans un objet de liste générique ou un autre objet de collection. Si vous affichez les données, vous pouvez lier l’interface utilisateur à la collection.  
  
## <a name="dataset-workflow"></a>Jeu de données de flux de travail  
 Visual Studio fournit de nombreux outils pour simplifier l’utilisation des jeux de données. Le flux de travail de bout en bout de base est la suivante :  
  
-   Utilisez le **Source de données** fenêtre pour créer un nouveau jeu de données à partir d’une ou plusieurs sources de données. Utilisez le **Concepteur de Dataset** pour configurer le jeu de données et définir ses propriétés. Par exemple, vous devez spécifier les tables à partir de la source de données à inclure et les colonnes de chaque table. Choisissez avec soin préserver la quantité de mémoire qui nécessite le jeu de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Spécifier les relations entre les tables afin que les clés étrangères sont traitées correctement. Pour plus d’informations, consultez [remplir des jeux de données à l’aide des TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Utilisez le **Assistant Configuration de TableAdapter** pour spécifier la requête ou la procédure stockée qui remplit le groupe de données et les opérations de base de données (mise à jour, supprimer et ainsi de suite) à implémenter. Pour plus d'informations, voir ces rubriques :  
  
    -   [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Modifier des données dans des datasets](../data-tools/edit-data-in-datasets.md)  
  
    -   [Valider les données dans des datasets](../data-tools/validate-data-in-datasets.md)  
  
    -   [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)  
  
-   Interroger et rechercher les données dans le jeu de données. Pour plus d’informations, consultez [jeux de données de requête](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]permet de [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d) sur les données dans un <xref:System.Data.DataSet> objet. Pour plus d’informations, [consultez LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Utilisez le **des Sources de données** fenêtre pour lier des contrôles d’interface utilisateur pour le jeu de données ou des colonnes individuelles et pour spécifier les colonnes qui sont modifiables par l’utilisateur. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Architecture multicouche et de jeux de données  
 Pour plus d’informations sur les jeux de données dans les applications multicouches, consultez [travailler avec les jeux de données dans les applications multicouches](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Jeux de données et XML  
 Pour plus d’informations sur la conversion des jeux de données vers et à partir de XML, consultez [lit les données XML dans un dataset](../data-tools/read-xml-data-into-a-dataset.md) et [enregistrer un jeu de données au format XML](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)