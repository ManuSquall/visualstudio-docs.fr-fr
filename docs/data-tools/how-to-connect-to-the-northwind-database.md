---
title: "Comment&#160;: se connecter &#224; la base de donn&#233;es Northwind | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "connexions (Visual Studio), base de données Northwind"
  - "Northwind (exemple de base de données)"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: se connecter &#224; la base de donn&#233;es Northwind
Pour apprendre à créer des applications de base de données à l'aide de Visual Studio, vous allez devoir vous connecter à la base de données Northwind pour suivre de nombreux exemples figurant dans la documentation de ce produit.  Selon l'exemple choisi, vous vous connecterez à la base de données dans SQL Server ou un fichier de base de données, tel qu'un fichier pour Microsoft Access ou SQL Server.  
  
## Création de connexions de données à la base de données Northwind  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour créer une connexion de données à la base de données Northwind \(SQL Server\)  
  
1.  Dans le menu **Affichage**, choisissez **Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, ouvrez le menu contextuel de **Connexions de données**, puis choisissez **Ajouter une connexion**.  
  
     Une fois que vous avez choisi **Ajouter une connexion**, la boîte de dialogue **Choisir la source de données** ou **Ajouter une connexion** apparaît.  
  
3.  Si la boîte de dialogue **Choisir la source de données** s'affiche, sélectionnez **Microsoft SQL Server**, puis **OK**.  
  
     Si la boîte de dialogue **Ajouter une connexion** apparaît et que la **Source de données** n'est pas **Microsoft SQL Server \(SqlClient\)**, choisissez le bouton **Modifier** pour ouvrir la boîte de dialogue **Modifier la source de données**, sélectionnez **Microsoft SQL Server**, puis choisissez le bouton **OK**.  
  
4.  Dans la liste **Nom du serveur**, spécifiez le nom du serveur sur lequel se trouve la base de données Northwind.  
  
5.  Selon les spécifications de votre version de SQL Server et de la base de données Northwind, choisissez **Utiliser l'authentification Windows** ou **Utiliser l'authentification SQL Server**, et entrez un nom d'utilisateur et un mot de passe pour vous connecter à l'ordinateur exécutant SQL Server.  
  
6.  Choisissez la base de données Northwind dans la liste **Sélectionner ou entrer un nom de base de données**.  
  
7.  Choisissez **Tester la connexion** pour vérifier la connectivité à la base de données Northwind.  
  
8.  Cliquez sur **OK**.  
  
     Une connexion de données à la base de données Northwind est ajoutée à l'**Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
 Outre la connexion à une instance distante d'une base de données SQL Server, vous pouvez aussi vous connecter directement aux fichiers réels contenant la base de données.  Cela vous permet d'ajouter les fichiers de base de données directement à un projet où ils peuvent être déployés en tant que composants de l'application.  Les fichiers de base de données locaux suivants sont actuellement pris en charge : fichiers de base de données SQL Server Compact \(.sdf\), fichiers de base de données [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] et SQL Server Express \(.mdf\) et les fichiers de base de données Microsoft Access \(.mdb ou .accdb\).  
  
#### Pour créer une connexion de données à la base de données Northwind \- fichier de base de données SQL Server \(.mdf\)  
  
1.  Dans le menu **Affichage**, choisissez **Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, ouvrez le menu contextuel de **Connexions de données**, puis choisissez **Ajouter une connexion**.  
  
     Une fois que vous avez choisi **Ajouter une connexion**, la boîte de dialogue **Ajouter une connexion** ou **Choisir la source de données** apparaît.  
  
3.  Si la boîte de dialogue **Choisir la source de données** s'affiche, sélectionnez **Fichier de base de données Microsoft SQL Server**, puis **OK**.  
  
4.  Si la boîte de dialogue **Ajouter une connexion** apparaît, vérifiez que la **Source de données** est définie sur **Fichier de base de données Microsoft SQL Server \(SqlClient\)**.  Si elle n'est pas définie sur **Fichier de base de données Microsoft SQL Server \(SqlClient\)**, choisissez **Modifier** pour ouvrir la boîte de dialogue **Modifier la source de données**, choisissez **Fichier de base de données Microsoft SQL Server**, puis le bouton **OK**.  
  
5.  Choisissez **Parcourir** pour rechercher le fichier .mdf contenant la base de données Northwind.  
  
6.  Selon les spécifications de votre version de la base de données Northwind, choisissez **Utiliser l'authentification Windows** ou **Utiliser l'authentification SQL Server**, et entrez un nom d'utilisateur et un mot de passe pour vous connecter à l'ordinateur exécutant SQL Server.  
  
7.  Sélectionnez le bouton **OK**.  
  
     Une connexion de données à la base de données Northwind est ajoutée à l'**Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] comprend des modifications qui s'appliquent au fichier de base de données Northwind \(.mdf\).  Pour plus d'informations, voir [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md).  
  
#### Pour créer une connexion de données à la base de données Northwind – Fichier de base de données Access \(.mdb ou .accdb\)  
  
1.  Dans le menu **Affichage**, choisissez **Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
2.  Dans l'**Explorateur de serveurs**\/**Explorateur de bases de données**, ouvrez le menu contextuel de **Connexions de données**, puis choisissez **Ajouter une connexion**.  
  
     Une fois que vous avez choisi **Ajouter une connexion**, la boîte de dialogue **Ajouter une connexion** ou **Choisir la source de données** apparaît.  
  
3.  Si la boîte de dialogue **Choisir la source de données** s'affiche, sélectionnez **Fichier de base de données Microsoft Access**, puis **OK**.  
  
4.  Si la boîte de dialogue **Ajouter une connexion** apparaît, vérifiez que la **Source de données** est définie sur **Fichier de base de données Microsoft Access**.  Si elle n'est pas définie sur **Fichier de base de données Microsoft Access**, choisissez **Modifier** pour ouvrir la boîte de dialogue **Modifier la source de données**, choisissez **Fichier de base de données Microsoft Access**, puis le bouton **OK**.  
  
5.  Choisissez **Parcourir** pour rechercher le fichier .mdb ou .accdb contenant la base de données Northwind.  
  
6.  Entrez un nom d'utilisateur et un mot de passe si votre version de la base de données Northwind le requiert.  
  
7.  Cliquez sur **OK**.  
  
     Une connexion de données à la base de données Northwind est ajoutée à l'**Explorateur de serveurs**\/**Explorateur de bases de données**.  
  
## Voir aussi  
 [Comment : installer des exemples de bases de données](../data-tools/how-to-install-sample-databases.md)   
 [Programmation de données avec Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)