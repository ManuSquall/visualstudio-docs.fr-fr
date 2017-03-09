---
title: "Comment&#160;: mettre &#224; niveau LocalDB ou continuer avec SQL Server Express | Microsoft Docs"
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
  - "LocalDB"
  - "SQL Server Express"
  - "LocalDB du SQL Server"
  - "SQLEXPRESS"
  - "mettre à niveau de SQLExpress vers SQLExpress"
  - "mettre à niveau vers LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: mettre &#224; niveau LocalDB ou continuer avec SQL Server Express
Cette rubrique décrit les options pour mettre à jour votre base de données \(.mdf\) après avoir installé [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] et inclut des instructions pour les tâches suivantes :  
  
-   Mettez à niveau une base de données à utiliser LocalDB  
  
-   Mettez à niveau une base de données à utiliser une version plus récente de SQL Server Express  
  
-   Le travail à une base de données dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] mais conserver la compatibilité avec [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]  
  
-   Faites de SQL Server Express le moteur de base de données par défaut  
  
 Vous pouvez utiliser [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] pour ouvrir un projet contenant une base de données \(.mdf\) créée à l'aide d'une version antérieure de SQL Server Express.  Toutefois, pour continuer à développer votre projet dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], vous devez soit avoir cette version de SQL Server Express est installé sur le même ordinateur que Visual Studio, vous devez mettre à niveau la base de données pour utiliser SQL Server Express LocalDB.  Si vous améliorez la base de données, vous ne pourrez pas accéder avec les versions antérieures de SQL Server Express.  
  
 Vous pouvez également être invité à mettre à niveau une base de données créée à l'aide de [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] si la version du fichier n'est pas compatible avec l'instance de SQL Server Express est actuellement installée.  Pour résoudre le problème, Visual Studio vous invite à mettre à niveau le fichier vers la dernière version de SQL Server Express.  
  
> [!IMPORTANT]
>  Il est recommandé de sauvegarder la base de données avant de la mettre à niveau.  
  
 Avant de mettre à niveau une base de données, vous devez considérer les critères suivants :  
  
-   N'effectuez pas si vous souhaitez utiliser sur votre projet dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] et [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
-   N'effectuez pas si votre application est utilisée dans les environnements qui utilisent SQL Server Express plutôt que LocalDB.  
  
-   N'effectuez pas si votre application utilise des connexions distantes car les LocalDB ne reçoit pas.  
  
-   N'effectuez pas si votre application compte sur internet information services \(IIS\).  
  
-   Envisagez de mettre à jour si vous souhaitez aux applications de base de données de test dans un environnement de bac à sable \(sandbox\) mais ne souhaitez pas gérer une base de données.  
  
### Pour mettre à niveau une base de données à utiliser LocalDB  
  
1.  Dans **Explorateur de serveurs**, choisissez le bouton **Connexion à une base de données** .  
  
2.  Dans la boîte de dialogue **Ajouter une connexion** , spécifiez les informations suivantes :  
  
    -   **source de données :** Microsoft SQL Server \(SqlClient\)  
  
    -   **nom du serveur :** \) \(LocalDB \\ v11.0  
  
    -   **Attachez une base de données :** *Chemin d'accès*, où *Chemin d'accès* est le chemin d'accès physique au fichier principal .mdf.  
  
    -   **nom logique :** *Nom*, où *Nom* est le nom que vous souhaitez utiliser avec le fichier.  
  
3.  Choisissez le bouton **OK** .  
  
4.  Lorsque vous êtes invité, cliquez sur le bouton **oui** pour améliorer le fichier.  
  
 La base de données est mise à jour, joint au moteur de base de données de LocalDB, etc. compatible avec [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)].  
  
 Vous pouvez également modifier une connexion de SQLExpress pour utiliser LocalDB en ouvrant le menu contextuel pour la connexion et en choisissant **Modifier la connexion**.  Dans **Modifier la connexion** boîte de dialogue, remplacez nom du serveur en\) \(LocalDB \\ v11.0.  Dans la boîte de dialogue **Propriétés avancées** , assurez \-vous que **instance utilisateur** a la valeur False.  
  
### Pour mettre à niveau vers une nouvelle version de SQL Server Express  
  
1.  Dans le menu contextuel pour la connexion à la base de données, choisissez **Modifier la connexion**.  
  
2.  Dans la boîte de dialogue **Modifier la connexion** , choisissez le bouton **Avancé** .  
  
3.  Dans la boîte de dialogue **Propriétés avancées** , choisissez le bouton **OK** sans modifier le nom du serveur.  
  
 La base de données est mise à jour pour correspondre à la version actuelle d' [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)].  
  
### Pour utiliser la base de données dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] mais conserver la compatibilité avec [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]  
  
1.  Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], ouvrez le projet sans le mettre à jour.  
  
    -   Pour exécuter le projet, choisissez la touche F5.  
  
    -   Pour modifier la base de données, ouvrez le fichier .mdf dans **Explorateur de solutions**, puis développez le nœud dans **Explorateur de serveurs** pour utiliser votre base de données comme vous avez effectué dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
### Pour rendre SQL Server Express le moteur de base de données par défaut  
  
1.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  
  
2.  Dans la boîte de dialogue **Options** , développez les options **Outils de données** , puis sélectionnez le nœud **Connexions de données** .  
  
3.  Dans la zone de texte **Nom de l'instance de SQL Server** , spécifiez le nom de l'instance SQL Server Express que vous souhaitez utiliser.  Si l'instance n'est pas appelée, spécifiez `. \SQLEXPRESS`.  
  
4.  Choisissez le bouton **OK** .  
  
 SQL Server Express sera le moteur de base de données par défaut pour vos applications.  
  
## Voir aussi  
 [Vue d'ensemble des données locales](../data-tools/local-data-overview.md)   
 [Procédure pas à pas : connexion à des données dans un fichier de base de données local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)