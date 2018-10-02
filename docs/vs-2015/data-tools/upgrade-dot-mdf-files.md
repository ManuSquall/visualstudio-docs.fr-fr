---
title: Mettre à niveau les fichiers .mdf | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 773f88e34c111b44f92080c3117eb7e2e42dd70c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503027"
---
# <a name="upgrade-mdf-files"></a>Mettre à jour des fichiers .mdf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [mettre à niveau les fichiers .mdf](https://docs.microsoft.com/visualstudio/data-tools/upgrade-dot-mdf-files).  
  
  
Cette rubrique décrit les options de mise à niveau de votre fichier de base de données (.mdf) après avoir installé une version plus récente de Visual Studio. Il inclut des instructions pour les tâches suivantes :  
  
-   Mise à niveau d’un fichier de base de données pour utiliser une version plus récente de SQL Server Express LocalDB  
  
-   Mise à niveau d’un fichier de base de données pour utiliser une version plus récente de SQL Server Express  
  
-   Travailler avec un fichier de base de données dans Visual Studio, mais conserver la compatibilité avec une version antérieure de SQL Server Express ou LocalDB  
  
-   Vérifiez SQL Server Express le moteur de base de données par défaut  
  
 Vous pouvez utiliser Visual Studio pour ouvrir un projet qui contient un fichier de base de données (.mdf) qui a été créé à l’aide d’une version antérieure de SQL Server Express ou LocalDB. Toutefois, pour continuer à développer votre projet dans Visual Studio, vous devez disposer de cette version de SQL Server Express ou LocalDB est installée sur le même ordinateur que Visual Studio, ou vous devez mettre à niveau le fichier de base de données. Si vous mettez à niveau le fichier de base de données, vous ne pourrez pas y accéder à l’aide de versions antérieures de SQL Server Express ou LocalDB.  
  
 Vous pouvez également être invité à mettre à niveau d’un fichier de base de données qui a été créé via une version antérieure de SQL Server Express ou LocalDB si la version du fichier n’est pas compatible avec l’instance de SQL Server Express ou LocalDB qui est actuellement installée. Pour résoudre ce problème, Visual Studio vous invite à mettre à niveau le fichier.  
  
> [!IMPORTANT]
>  Nous vous recommandons de sauvegarder le fichier de base de données avant de vous mettre à niveau.  
  
> [!WARNING]
>  Si vous mettez à niveau un fichier .mdf qui a été créé dans la base de données locale 2014 (V12) 32 bits vers LocalDB 2016 (V13), vous ne serez pas en mesure d’ouvrir le fichier à nouveau dans la version 32 bits de LocalDB.  Dans la mise à jour 2, LocalDB V13 est 64 bits uniquement.  
  
 Avant de vous mettre à niveau une base de données, tenez compte des critères suivants :  
  
-   Ne pas mettre à niveau si vous souhaitez travailler sur votre projet dans une version antérieure et une version plus récente de Visual Studio.  
  
-   Ne pas mettre à niveau si votre application doit être utilisée dans les environnements qui utilisent SQL Server Express plutôt que LocalDB.  
  
-   Ne pas mettre à niveau si votre application utilise des connexions à distance, car la base de données locale n’accepte pas les.  
  
-   Ne pas mettre à niveau si votre application s’appuie sur les Services Internet (IIS).  
  
-   Envisagez la mise à niveau si vous souhaitez tester des applications de base de données dans un environnement de bac à sable mais que vous ne souhaitez pas administrer une base de données.  
  
### <a name="to-upgrade-a-database-file"></a>Pour mettre à niveau d’un fichier de base de données  
  
1.  Dans **Explorateur de serveurs**, sélectionnez le **se connecter à la base de données** bouton.  
  
2.  Dans le **ajouter une connexion** boîte de dialogue, spécifiez les informations suivantes :  
  
    -   **Source de données**: `Microsoft SQL Server (SqlClient)`  
  
    -   **Nom du serveur**:  
  
        -   Pour utiliser la version par défaut : `(localdb)\MSSQLLocalDB`.  Elle permet d’indiquer ProjectV12 ou ProjectV13, selon la version de Visual Studio est installée et lorsque la première instance de base de données locale a été créée. Le **MSSQLLocalDB** nœud **Explorateur d’objets SQL Server** montre de quelle version il pointe vers.  
  
        -   Pour utiliser une version spécifique : `(localdb)\ProjectsV12` ou `(localdb)\ProjectsV13`, où V12 est LocalDB 2014 et V13 est LocalDB 2016.  
  
    -   **Attacher un fichier de base de données**: le chemin d’accès physique du fichier .mdf principal.  
  
    -   **Nom logique**: le nom que vous souhaitez utiliser avec le fichier.  
  
3.  Sélectionnez le bouton **OK**.  
  
4.  Lorsque vous y êtes invité, sélectionnez le **Oui** bouton pour mettre à niveau le fichier.  
  
 La base de données est mis à niveau est attaché au moteur de base de données LocalDB et n’est plus compatible avec l’ancienne version de base de données locale.  
  
 Vous pouvez également modifier une connexion SQL Server Express pour utiliser la base de données locale en ouvrant le menu contextuel pour la connexion, puis en sélectionnant **modifier la connexion**. Dans le **modifier la connexion** boîte de dialogue, changez le nom du serveur à `(LocalDB)\MSSQLLocalDB`. Dans le **propriétés avancées** boîte de dialogue zone, assurez-vous que l’option **Instance utilisateur** a la valeur **False**.  
  
### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>Mise à niveau vers une version plus récente de SQL Server Express  
  
1.  Dans le menu contextuel pour la connexion à la base de données, sélectionnez **modifier la connexion**.  
  
2.  Dans le **modifier la connexion** boîte de dialogue, sélectionnez le **avancé** bouton.  
  
3.  Dans le **propriétés avancées** boîte de dialogue, sélectionnez le **OK** bouton sans modifier le nom du serveur.  
  
 Le fichier de base de données est mis à niveau pour correspondre à la version actuelle de SQL Server Express.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Pour fonctionner avec la base de données dans Visual Studio, tout en continuant la compatibilité avec SQL Server Express  
  
-   Dans Visual Studio, ouvrez le projet sans la mise à niveau.  
  
    -   Pour exécuter le projet, sélectionnez la touche F5.  
  
    -   Pour modifier la base de données, ouvrez le fichier .mdf dans **l’Explorateur de solutions**, puis développez le nœud dans **Explorateur de serveurs** pour travailler avec votre base de données.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Pour rendre SQL Server Express le moteur de base de données par défaut  
  
1.  Dans la barre de menus, sélectionnez **outils** > **Options**.  
  
2.  Dans le **Options** boîte de dialogue, développez le **Data Tools** options, puis sélectionnez le **des connexions de données** nœud.  
  
3.  Dans le **nom de l’Instance SQL Server** texte, spécifiez le nom de l’instance de SQL Server Express ou de la base de données locale que vous souhaitez utiliser. Si l’instance n’est pas nommée, spécifiez `.\SQLEXPRESS or (localdb)\MSSQLLocalDB`.  
  
4.  Sélectionnez le bouton **OK**.  
  
 SQL Server Express sera le moteur de base de données par défaut pour vos applications.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des données locales](../data-tools/local-data-overview.md)   
 [Procédure pas à pas : connexion à des données dans un fichier de base de données local (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)

