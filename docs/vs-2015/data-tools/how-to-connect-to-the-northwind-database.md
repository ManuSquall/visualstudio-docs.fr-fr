---
title: 'Comment : se connecter à la base de données Northwind | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2b4393758b4c246af0da830b6ed8d8e20eb8ff40
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191124"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Comment : se connecter à la base de données Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour apprendre à créer des applications de base de données à l'aide de Visual Studio, vous allez devoir vous connecter à la base de données Northwind pour suivre de nombreux exemples figurant dans la documentation de ce produit. Selon l'exemple choisi, vous vous connecterez à la base de données dans SQL Server ou un fichier de base de données, tel qu'un fichier pour Microsoft Access ou SQL Server.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Création de connexions de données à la base de données Northwind  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>Pour créer une connexion de données à la base de données Northwind (SQL Server)  
  
1.  Sur le **vue** menu, choisissez **Explorateur de serveurs**/**Database Explorer**.  
  
2.  Dans **Explorateur de serveurs**/**Database Explorer**, ouvrez le menu contextuel pour **des connexions de données** et choisissez **ajouter une connexion**.  
  
     Après avoir choisi **ajouter une connexion**, soit le **choisir la Source de données** boîte de dialogue ou la **ajouter une connexion** boîte de dialogue s’affiche.  
  
3.  Si le **choisir la Source de données** boîte de dialogue s’affiche, sélectionnez **Microsoft SQL Server**, puis choisissez **OK**.  
  
     Si le **ajouter une connexion** boîte de dialogue s’affiche et le **source de données** n’est pas **Microsoft SQL Server (SqlClient)**, choisissez le **modification** bouton pour ouvrir la **modifier la Source de données** boîte de dialogue, sélectionnez **Microsoft SQL Server**, puis choisissez le **OK** bouton.  
  
4.  Dans le **nom du serveur** liste, spécifiez le nom du serveur sur lequel se trouve la base de données Northwind.  
  
5.  Selon les besoins de votre version de SQL Server et la base de données Northwind, choisissez **utiliser l’authentification Windows** ou choisissez **utiliser l’authentification de serveur SQL** et entrez un nom d’utilisateur et mot de passe pour vous connecter à l’ordinateur qui exécute SQL Server.  
  
6.  Choisissez la base de données Northwind dans la **sélectionner ou entrer un nom de base de données** liste.  
  
7.  Choisissez **tester la connexion** pour vérifier la connectivité à la base de données Northwind.  
  
8.  Cliquez sur **OK**.  
  
     Une connexion de données à la base de données Northwind est ajoutée à **Explorateur de serveurs**/**Database Explorer**.  
  
 Outre la connexion à une instance distante d'une base de données SQL Server, vous pouvez aussi vous connecter directement aux fichiers réels contenant la base de données. Cela vous permet d'ajouter les fichiers de base de données directement à un projet où ils peuvent être déployés en tant que composants de l'application. Les fichiers de base de données locale suivants sont actuellement gérées : fichiers de base de données SQL Server Compact (.sdf), [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les fichiers de base de données SQL Server Express (.mdf) et les fichiers de base de données Microsoft Access (.mdb ou .accdb).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>Pour créer une connexion de données à la base de données Northwind - fichier de base de données SQL Server (.mdf)  
  
1.  Sur le **vue** menu, choisissez **Explorateur de serveurs**/**Database Explorer**.  
  
2.  Dans **Explorateur de serveurs**/**Database Explorer**, ouvrez le menu contextuel pour **des connexions de données** et choisissez **ajouter une connexion**.  
  
     Après avoir choisi **ajouter une connexion**, soit le **ajouter une connexion** boîte de dialogue ou la **choisir la Source de données** boîte de dialogue s’affiche.  
  
3.  Si le **choisir la Source de données** boîte de dialogue s’affiche, sélectionnez **fichier de base de données Microsoft SQL Server**, puis choisissez le **OK**.  
  
4.  Si le **ajouter une connexion** boîte de dialogue s’affiche, vérifiez que le **source de données** a la valeur **fichier de base de données Microsoft SQL Server (SqlClient)**. Si elle n’est pas définie sur **fichier de base de données Microsoft SQL Server (SqlClient)**, choisissez **modification** pour ouvrir le **modifier la Source de données** boîte de dialogue, sélectionnez **Microsoft SQL Fichier de base de données de serveur**, puis choisissez le **OK** bouton.  
  
5.  Choisissez **Parcourir** pour localiser le fichier .mdf qui contient la base de données Northwind.  
  
6.  Selon les besoins de votre version de la base de données Northwind, choisissez **utiliser l’authentification Windows** ou choisissez **l’authentification SQL Server** et entrez un nom d’utilisateur et le mot de passe pour ouvrir une session sur le ordinateur exécutant SQL Server.  
  
7.  Sélectionnez le bouton **OK** .  
  
     Une connexion de données à la base de données Northwind est ajoutée à **Explorateur de serveurs**/**Database Explorer**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] comprend des modifications qui s'appliquent au fichier de base de données Northwind (.mdf). Pour plus d’informations, consultez [Comment : installer Sample Databases](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>Pour créer une connexion de données à la base de données Northwind – Fichier de base de données Access (.mdb ou .accdb)  
  
1.  Sur le **vue** menu, choisissez **Explorateur de serveurs**/**Database Explorer**.  
  
2.  Dans **Explorateur de serveurs**/**Database Explorer**, ouvrez le menu contextuel pour **des connexions de données** et choisissez **ajouter une connexion**.  
  
     Après avoir choisi **ajouter une connexion**, soit le **ajouter une connexion** boîte de dialogue ou la **choisir la Source de données** boîte de dialogue s’affiche.  
  
3.  Si le **choisir la Source de données** boîte de dialogue s’affiche, sélectionnez **fichier de base de données Microsoft Access**, puis choisissez **OK**.  
  
4.  Si le **ajouter une connexion** boîte de dialogue s’affiche, vérifiez que le **source de données** a la valeur **fichier de base de données Microsoft Access**. Si elle n’est pas définie sur **fichier de base de données Microsoft Access**, choisissez **modification** pour ouvrir le **modifier la Source de données** boîte de dialogue, sélectionnez **base de données Microsoft Access Fichier**, puis choisissez le **OK** bouton.  
  
5.  Choisissez **Parcourir** pour localiser le fichier .mdb ou .accdb contenant la base de données Northwind.  
  
6.  Entrez un nom d'utilisateur et un mot de passe si votre version de la base de données Northwind le requiert.  
  
7.  Cliquez sur **OK**.  
  
     Une connexion de données à la base de données Northwind est ajoutée à **Explorateur de serveurs**/**Database Explorer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : installer les exemples de bases de données](../data-tools/how-to-install-sample-databases.md)   
 [Programmation de données avec Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Procédures pas à pas de données](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)