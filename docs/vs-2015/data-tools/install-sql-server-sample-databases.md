---
title: Installer des exemples de bases de données SQL Server | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3991d3b741162b4b1993e5359ad427c17f00321a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651529"
---
# <a name="install-sql-server-sample-databases"></a>Installer des bases de données SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les exemples de bases de données sont utiles pour expérimenter les requêtes SQL et LINQ, la liaison de données, la modélisation Entity Framework, etc.  Chaque produit de base de données a ses propres exemples de bases de données. Northwind et AdventureWorks sont deux exemples de bases de données populaires SQL Server.

 **AdventureWorks** est l’exemple de base de données actuel fourni pour les produits SQL Server. Vous pouvez le télécharger sous la forme d’un fichier. mdf à partir de la [page AdventureWorks sur CodePlex](http://msftdbprodsamples.codeplex.com/). Des versions régulières et légères de la base de données sont disponibles ici. Pour la plupart des scénarios, la version LT est préférable, car elle est moins complexe.

 **Northwind** est une base de données SQL Server relativement simple qui a été utilisée depuis de nombreuses années. Vous pouvez le télécharger sous la forme d’un fichier. bak à partir de la [page base de données Northwind sur CodePlex](https://northwinddatabase.codeplex.com/). Pour éviter les problèmes d’autorisations, décompressez le fichier dans un nouveau dossier qui ne se trouve pas dans votre dossier utilisateur.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Pour restaurer une base de données à partir d’un fichier. bak dans Visual Studio

1. Lorsque vous sauvegardez une base de données Microsoft SQL Server, le résultat est un fichier. bak. Pour que le fichier. bak soit à nouveau utilisable comme fichier de base de données, il doit être *restauré*. Dans le menu principal, sélectionnez **afficher**  > **Explorateur d’objets SQL Server**. Si vous ne le voyez pas, vous devrez peut-être l’installer. Accédez au **panneau de configuration**  > **programmes et fonctionnalités**, recherchez Microsoft Visual Studio 2015, puis cliquez sur le bouton **modifier** . Lorsque la liste des composants installés s’affiche dans la fenêtre installer, activez la case à cocher **Explorateur d’objets SQL Server** , puis poursuivez l’installation.

2. Dans Explorateur d’objets SQL Server, cliquez avec le bouton droit sur n’importe quel moteur de base de données SQL Server (par exemple, la base de données locale), puis sélectionnez**nouvelle requête**.

     ![Explorateur d’objets SQL Server une nouvelle requête](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata Explorateur d’objets SQL Server nouvelle requête")

3. Tout d’abord, vous avez besoin des noms logiques de la base de données et des fichiers journaux dans le fichier. bak. Pour ce faire, entrez la requête suivante dans l’éditeur de requête SQL, puis sélectionnez le bouton vert **Run** en haut de la fenêtre. Modifiez le chemin d’accès du fichier si nécessaire pour pointer vers le fichier. bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Notez les noms logiques qui s’affichent dans la fenêtre résultats.  Pour la base de données Northwind, les deux noms logiques sont Northwind et Northwind_log.

4. À présent, exécutez cette requête pour créer la base de données. Remplacez les chemins source et de destination, les noms de bases de données logiques et les noms de fichiers physiques de Northwind, le cas échéant. Conservez les extensions de fichier. mdf et. ldf.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. Dans Explorateur d’objets SQL Server, cliquez avec le bouton droit sur le nœud **bases de données** et le nœud base de données Northwind doit s’afficher. Si ce n’est pas le cas, cliquez avec le bouton droit sur bases de données, puis sélectionnez **Ajouter une nouvelle base de données**. Entrez le nom et l’emplacement du fichier. mdf que vous venez de créer.

6. La base de données est maintenant prête à être utilisée comme source de données dans Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Pour restaurer une base de données à partir d’un fichier. bak dans SQL Server Management Studio

1. Téléchargez SQL Server Management Studio à partir du site de téléchargement.

2. Dans la fenêtre de l' **Explorateur d’objets** de SSMS, cliquez avec le bouton droit sur le nœud **bases de données** , sélectionnez**restaurer la base de données**, puis indiquez l’emplacement du fichier. bak.

     ![Base de données de restauration SSMS](../data-tools/media/raddata-ssms-restore-database.png "Base de données de restauration raddata SSMS")
