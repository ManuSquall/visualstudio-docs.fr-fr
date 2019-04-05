---
title: Outils de jeu de données
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 723b074b51e97282f67a8e490ec6b109e765dbc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949693"
---
# <a name="dataset-tools-in-visual-studio"></a>Outils de dataset dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


REMARQUE]
>  Jeux de données et les classes connexes sont des technologies .NET héritées à partir du début des années 2000 qui permettent aux applications d’utiliser les données en mémoire, tandis que les applications sont déconnectées de la base de données. Ils sont particulièrement utiles pour les applications qui permettent aux utilisateurs de modifier des données et conserver les modifications apportées à la base de données. Bien que les jeux de données s’est avérés une technologie très réussie, nous recommandons d’utilisent Entity Framework nouvelles applications .NET. Entity Framework fournit un moyen plus naturel pour travailler avec des données tabulaires en tant que modèles d’objet, et elle possède une interface de programmation plus simple.

 Un objet de jeu de données est un objet en mémoire qui est essentiellement un mini-de base de données. Il contient des objets DataRow, DataTable et DataColumn dans lequel vous pouvez stocker et modifier des données à partir d’une ou plusieurs bases de données sans avoir à maintenir une connexion ouverte. Le jeu de données conserve les informations sur les modifications apportées à ses données, afin de mises à jour peuvent être suivies et renvoyées à la base de données lorsque votre application est reconnectée.

 Jeux de données et les classes connexes sont définis dans l’espace de noms System.Data dans la bibliothèque de classes .NET Framework. Vous pouvez créer et modifier des jeux de données dynamiquement dans le code. Pour plus d’informations sur la marche à suivre, consultez ADO.NET. La documentation de cette section montre comment utiliser des jeux de données à l’aide des concepteurs de Visual Studio. Une chose à savoir : jeux de données qui est exécutées par les concepteurs d’utiliser les objets TableAdapter pour interagir avec la base de données, tandis que les jeux de données qui est effectuées par programme utilisent des objets DataAdapter. Pour plus d’informations sur la création de jeux de données par programmation, consultez [DataAdapters et DataReaders](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Si votre application doit uniquement lire les données à partir d’une base de données et n’effectue pas les mises à jour, ajoute ou supprime, vous pouvez généralement obtenir de meilleures performances à l’aide d’un objet DataReader pour récupérer des données dans un objet de liste générique ou un autre objet de collection. Si vous affichez les données, vous pouvez lier l’interface utilisateur à la collection.

## <a name="dataset-workflow"></a>Jeu de données de flux de travail
 Visual Studio fournit de nombreux outils pour simplifier l’utilisation des jeux de données. Le workflow de bout en bout de base est :

-   Utilisez le **Source de données** fenêtre pour créer un nouveau jeu de données à partir d’une ou plusieurs sources de données. Utilisez le **Concepteur de Dataset** pour configurer le jeu de données et définissez ses propriétés. Par exemple, vous devez spécifier les tables à partir de la source de données à inclure et quelles colonnes de chaque table. Choisissez soigneusement préserver la quantité de mémoire qui nécessite le jeu de données. Pour plus d’informations, consultez [Créer et configurer des datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Spécifier les relations entre les tables afin que les clés étrangères sont gérées correctement. Pour plus d’informations, consultez [remplir des jeux de données à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

-   Utilisez le **Assistant Configuration de TableAdapter** pour spécifier la requête ou la procédure stockée qui remplira le jeu de données et les opérations de base de données (update, delete et ainsi de suite) à implémenter. Pour plus d'informations, voir ces rubriques :

    -   [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

    -   [Modifier des données dans des datasets](../data-tools/edit-data-in-datasets.md)

    -   [Valider les données dans des datasets](../data-tools/validate-data-in-datasets.md)

    -   [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)

-   Interroger et rechercher les données dans le jeu de données. Pour plus d’informations, consultez [jeux de données de requête](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] permet de [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sur les données dans un <xref:System.Data.DataSet> objet. Pour plus d’informations, [consultez LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

-   Utilisez le **des Sources de données** fenêtre pour lier des contrôles d’interface utilisateur pour le jeu de données ou des colonnes individuelles et pour spécifier les colonnes qui sont modifiables par l’utilisateur. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Architecture de jeux de données et des applications multicouches
 Pour plus d’informations sur les jeux de données dans les applications multicouches, consultez [fonctionne avec les jeux de données dans les applications multicouches](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Jeux de données et XML
 Pour plus d’informations sur la conversion des jeux de données vers et à partir de XML, consultez [lit les données XML dans un dataset](../data-tools/read-xml-data-into-a-dataset.md) et [enregistrer un jeu de données au format XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Voir aussi
 [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
