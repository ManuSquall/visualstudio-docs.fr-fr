---
title: 'Comment : installer les bases de données exemple | Microsoft Docs'
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd51bd397e6db3728c10f52db68d45e226fb605b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251032"
---
# <a name="how-to-install-sample-databases"></a>Comment : installer des exemples de bases de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De nombreux exemples de données nécessitent de se connecter aux exemples de base de données Northwind, Pubs et AdventureWorks. Vous pouvez installer ces bases de données et vous y connecter en utilisant les procédures ci-dessous.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Installation des bases de données  
 De nombreux exemples de données requièrent la disponibilité d'exemples de bases de données qui peuvent être téléchargés à partir des sites web. Les exemples de bases de données incluent les bases de données AdventureWorks, Northwind et Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>Pour installer les exemples de base de données Northwind et Pubs pour SQL Server  
  
1.  Accédez à la [Northwind and Pubs Sample Databases](http://go.microsoft.com/fwlink?linkid=64296) site web.  
  
2.  Téléchargez et exécutez le programme d'installation.  
  
     Le programme d’installation ajoute un dossier **SQL Server 2000 Sample Databases** dans le dossier racine sur votre ordinateur. (Par exemple : **C:\SQL Server 2000 Sample Databases**).  
  
3.  Recherchez le script SQL pour la base de données voulue, Northwind ou Pubs.  
  
    > [!WARNING]
    >  Le fichier de base de données .MDF ne peut pas être facilement converti en un format utilisable dans les versions actuelles SQL Server. Il est donc préférable d'utiliser le script pour créer la base de données.  
  
4.  Dans **Explorateur de serveurs**, créer une connexion à une instance de SQL Server où vous souhaitez installer la base de données. Si vous ne disposez pas d'un serveur SQL Server spécifique, vous pouvez utiliser la base de données qui est installée automatiquement avec Visual Studio. Pour ce faire, spécifiez `(localdb)\v11.0` comme nom de serveur.  
  
     Pour créer la connexion, procédez comme suit :  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>Pour créer une connexion à une instance de SQL Server  
  
    1.  Dans **Explorateur de serveurs**, ouvrez le menu contextuel pour le **des connexions de données** nœud, puis choisissez **ajouter une connexion**.  
  
         Le **ajouter une connexion** boîte de dialogue s’affiche.  
  
    2.  Entrez le nom de l'instance SQL Server sur laquelle vous souhaitez créer la base de données Northwind ou Pubs ou entrez (localdb)\v11.0.  
  
    3.  Sous **sélectionner ou entrer un nom de base de données**, choisissez une base de données dans la liste, par exemple, tempdb.  
  
    4.  Choisissez le **tester la connexion** bouton pour vérifier que tout fonctionne, puis choisissez le **OK** bouton.  
  
         Un nouveau nœud de connexion apparaît dans **Explorateur de serveurs**.  
  
5.  Dans le menu contextuel du nœud de connexion pour votre serveur, puis choisissez le **nouvelle requête** bouton.  
  
     Une fenêtre d'éditeur s'ouvre et affiche un fichier script .sql vide.  
  
6.  Collez le contenu de instnwnd.sql ou instpubs.sql dans la fenêtre d'éditeur.  
  
7.  Cliquez sur le bouton d'exécution de la requête (icône en forme de triangle vert ouvert dans la partie supérieure droite de la fenêtre de requête).  
  
     Si la requête réussit, le message **commande (s) terminée** s’affiche. Cela signifie que la base de données Northwind ou Pubs a été créée.  
  
     Vous devez quand même ajouter une connexion à l'exemple de base de données. Dans **Explorateur de serveurs**, ouvrez le menu contextuel pour le **des connexions de données** nœud et choisissez **ajouter une connexion**.  
  
8.  Choisissez la même base de données serveur que vous avez choisi précédemment, mais cette fois, sous sélectionner ou entrer un nom de base de données, choisissez la base de données Northwind ou pubs et choisissez le **OK** bouton.  
  
     Un nouveau nœud apparaît sous connexions de données pour l'exemple de base de données.  
  
9. Fermez la fenêtre de l'éditeur et confirmez que vous ne voulez pas enregistrer le fichier de requête. Il n'est pas nécessaire d'enregistrer le script de création de la base de données une fois que vous avez créé la base de données.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>Pour installer les exemples de bases de données AdventureWorks  
  
-   Téléchargez les bases de données exemple AdventureWorks à partir de la [site CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Pour installer l'exemple de base de données Northwind pour Microsoft Access  
  
1.  Dans Microsoft Access 2010 ou version ultérieure, recherchez des modèles en ligne de Northwind, choisissez **base de données Desktop Northwind 2007 exemple**.  
  
2.  Dans Microsoft Access, enregistrez le fichier de la base de données sous Northwind.accdb.  
  
 La nouvelle extension pour les bases de données Access est .accdb. Consultez [programmation de données avec Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Pour vous connecter à la base de données Northwind en utilisant l’accès, consultez [Comment : se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Les exemples de bases de données sont fournis à titre d'illustration uniquement et ne présentent pas nécessairement les meilleures pratiques de sécurité.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment déterminer la version et l’édition de SQL Server et ses composants](http://support.microsoft.com/kb/321185)   
 [Créer une base de données SQL à l’aide d’un concepteur](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Guide pratique pour se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)