---
title: "Comment&#160;: installer des exemples de bases de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Adventure Works (exemple de base de données)"
  - "données (Visual Studio), exemples de bases de données"
  - "Northwind (exemple de base de données)"
  - "exemples de bases de données, Adventure Works"
  - "exemples de bases de données, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: installer des exemples de bases de donn&#233;es
De nombreux exemples de données nécessitent de se connecter aux exemples de base de données Northwind, Pubs et AdventureWorks.  Vous pouvez installer ces bases de données et vous y connecter en utilisant les procédures ci\-dessous.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Installation des bases de données  
 De nombreux exemples de données requièrent la disponibilité d'exemples de bases de données qui peuvent être téléchargés à partir des sites web.  Les exemples de bases de données incluent les bases de données AdventureWorks, Northwind et Pubs.  
  
#### Pour installer les exemples de base de données Northwind et Pubs pour SQL Server  
  
1.  Accédez au site web [Exemples de base de données Northwind et Pubs](http://go.microsoft.com/fwlink?linkid=64296).  
  
2.  Téléchargez et exécutez le programme d'installation.  
  
     Le programme d'installation ajoute un dossier **Exemples de base de données SQL Server 2000** au dossier racine sur votre ordinateur.  \(Par exemple : **C:\\SQL Server 2000 Sample Databases**\).  
  
3.  Recherchez le script SQL pour la base de données voulue, Northwind ou Pubs.  
  
    > [!WARNING]
    >  Le fichier de base de données .MDF ne peut pas être facilement converti en un format utilisable dans les versions actuelles SQL Server. Il est donc préférable d'utiliser le script pour créer la base de données.  
  
4.  Dans **Explorateur de serveurs**, créez une connexion à une instance de SQL Server sur lequel vous souhaitez installer la base de données.  Si vous ne disposez pas d'un serveur SQL Server spécifique, vous pouvez utiliser la base de données qui est installée automatiquement avec Visual Studio.  Pour cela, spécifiez `(localdb\v11.0` comme nom du serveur.  
  
     Pour créer la connexion, procédez comme suit :  
  
    ###### Pour créer une connexion à une instance de SQL Server  
  
    1.  Dans **Explorateur de serveurs**, ouvrez le menu contextuel du nœud **Connexions de données**, puis choisissez **Ajouter une connexion**.  
  
         La boîte de dialogue **Ajouter une connexion** s'affiche.  
  
    2.  Entrez le nom de l'instance SQL Server sur laquelle vous souhaitez créer la base de données Northwind ou Pubs ou entrez \(localdb\)\\v11.0.  
  
    3.  Sous **Sélectionner ou entrer un nom de base de données**, choisissez une base de données dans la liste, par exemple tempdb.  
  
    4.  Cliquez sur le bouton **Tester la connexion** pour vérifier que tout fonctionne, puis choisissez le bouton **OK**.  
  
         Un nouveau nœud de connexion apparaît dans **Explorateur de serveurs**.  
  
5.  Ouvrez le menu contextuel du nœud de connexion de votre serveur puis choisissez le bouton **Nouvelle requête**.  
  
     Une fenêtre d'éditeur s'ouvre et affiche un fichier script .sql vide.  
  
6.  Collez le contenu de instnwnd.sql ou instpubs.sql dans la fenêtre d'éditeur.  
  
7.  Cliquez sur le bouton d'exécution de la requête \(icône en forme de triangle vert ouvert dans la partie supérieure droite de la fenêtre de requête\).  
  
     Si la requête aboutit, le message **L'exécution des commandes s'est bien déroulée.** s'affiche.  Cela signifie que la base de données Northwind ou Pubs a été créée.  
  
     Vous devez quand même ajouter une connexion à l'exemple de base de données.  Dans l'**Explorateur de serveurs**, ouvrez le menu contextuel du nœud **Connexions de données**, puis choisissez **Ajouter une connexion**.  
  
8.  Cliquez sur le même serveur de bases de données que celui que vous avez choisi précédemment, mais cette fois, sous Sélectionner ou entrer un nom de base de données, sélectionnez la base de données Northwind ou Pubs et choisissez le bouton **OK**.  
  
     Un nouveau nœud apparaît sous connexions de données pour l'exemple de base de données.  
  
9. Fermez la fenêtre de l'éditeur et confirmez que vous ne voulez pas enregistrer le fichier de requête.  Il n'est pas nécessaire d'enregistrer le script de création de la base de données une fois que vous avez créé la base de données.  
  
#### Pour installer les exemples de bases de données AdventureWorks  
  
-   Téléchargez les exemples de bases de données AdventureWorks à partir du [site web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### Pour installer l'exemple de base de données Northwind pour Microsoft Access  
  
1.  Dans Microsoft Access 2010 ou version ultérieure, parcourez les modèles en ligne de Northwind et choisissez **Exemple de base de données Desktop Northwind 2007**.  
  
2.  Dans Microsoft Access, enregistrez le fichier de la base de données sous Northwind.accdb.  
  
 La nouvelle extension pour les bases de données Access est .accdb.  Consultez [Programmation de données avec Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx).  Pour vous connecter à la base de données Northwind à l'aide d'Access, consultez [Comment : se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## Sécurité .NET Framework  
 Les exemples de bases de données sont fournis à titre d'illustration uniquement et ne présentent pas nécessairement les meilleures pratiques de sécurité.  
  
## Voir aussi  
 [Détermination de la version et de l'édition de SQL Server et de ses composants](http://support.microsoft.com/kb/321185)   
 [Procédure pas à pas : création d'un fichier de base de données local dans Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Comment : se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)