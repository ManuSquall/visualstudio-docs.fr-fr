---
title: Installer les bases de données SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6cd9260f29d8e46f66e54fec8cb24ae6857eb05
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217861"
---
# <a name="install-sql-server-sample-databases"></a>Installer les bases de données SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bases de données exemple sont utiles pour tester les requêtes SQL et LINQ, la liaison de données, modélisation de Entity Framework et ainsi de suite.  Chaque produit de base de données a ses propres bases de données exemple. Northwind et AdventureWorks sont deux populaires exemple bases de données SQL.  
  
 **AdventureWorks** est la base de données exemple actuelle fournie pour les produits de SQL Server. Vous pouvez le télécharger en tant qu’un fichier .mdf à partir de la [page AdventureWorks sur Codeplex](http://msftdbprodsamples.codeplex.com/). Il existe des versions (LT) régulières et légers de la base de données disponible ici. La plupart des scénarios, la version LT est préférable car il est moins complexe.  
  
 **Northwind** est une base de données SQL Server relativement simple qui a été utilisé depuis de nombreuses années. Vous pouvez le télécharger sous forme de fichier .bak à partir de la [page de base de données Northwind sur CodePlex](https://northwinddatabase.codeplex.com/). Pour éviter des problèmes d’autorisations, décompressez le fichier dans un nouveau dossier qui n’est pas sous votre dossier utilisateur.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Pour restaurer une base de données à partir d’un fichier .bak dans Visual Studio  
  
1.  Lorsque vous sauvegardez une base de données Microsoft SQL Server, le résultat est un fichier .bak. Pour rendre le .bak fichier utilisable en tant qu’un fichier de base de données, il doit être *restauré*. Dans le menu principal, sélectionnez **vue** > **Explorateur d’objets SQL Server**. Si vous ne le voyez, vous devrez peut-être l’installer. Accédez à **le panneau de configuration** > **programmes et fonctionnalités**, recherchez Microsoft Visual Studio 2015, puis cliquez sur le **modification** bouton. Lorsque la liste des composants installés s’affiche dans la fenêtre du programme d’installation, sélectionnez le **Explorateur d’objets SQL Server** case à cocher et poursuivez l’installation.  
  
2.  Dans l’Explorateur d’objets SQL Server, cliquez sur n’importe quel moteur de base de données SQL Server (par exemple, localdb), puis sélectionnez**nouvelle requête**.  
  
     ![SQL Server, objet Explorer nouvelle requête](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server, objet Explorer nouvelle requête")  
  
3.  Tout d’abord, vous devez les noms logiques des base de données et les fichiers journaux dans le fichier .bak. Pour l’obtenir, entrez cette requête dans l’éditeur de requête SQL, puis sélectionnez le vert **exécuter** bouton en haut de la fenêtre. Modifiez le chemin d’accès de fichier si nécessaire pour pointer vers le fichier .bak.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Notez les noms logiques qui s’affichent dans la fenêtre des résultats.  Pour la base de données Northwind, les deux noms logiques sont Northwind_log et Northwind.  
  
4.  Exécutez maintenant cette requête pour créer la base de données. Remplacez par votre propre des chemins d’accès source et de destination, les noms de base de données logique et les noms de fichiers physiques pour Northwind comme il convient. Conserver les fichiers .mdf et .ldf extensions de fichier.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  Dans l’Explorateur d’objets SQL Server, cliquez sur le **bases de données** nœud, vous devriez voir le nœud de base de données Northwind. Dans le cas contraire, puis avec le bouton droit sur bases de données, puis sélectionnez **ajouter une nouvelle base de données**. Entrez le nom et l’emplacement du fichier .mdf que vous venez de créer.  
  
6.  La base de données est maintenant prêt à utiliser comme source de données dans Visual Studio.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Pour restaurer une base de données à partir d’un fichier .bak dans SQL Server Management Studio  
  
1.  Télécharger SQL Server Management Studio à partir du site de téléchargement.  
  
2.  Dans SSMS **Explorateur d’objets** fenêtre, avec le bouton droit le **bases de données** nœud, sélectionnez**Restore Database**et indiquer l’emplacement du fichier .bak.  
  
     ![SSMS Restore Database](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS Restore Database")

