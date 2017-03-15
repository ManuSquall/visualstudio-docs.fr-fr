---
title: "Vue d&#39;ensemble des donn&#233;es locales | Microsoft Docs"
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
  - "Access, fichiers .mdb dans Visual Studio"
  - "données (Visual Studio), locaux"
  - "accès aux données (Visual Studio), dépanner"
  - "données locales"
  - "LocalDB"
  - "SQL Express"
  - "SQL Server Compact"
  - "SQL Server Express"
  - "LocalDB du SQL Server"
  - "SQL Server, données locales"
  - "SQLEXPRESS"
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
caps.handback.revision: 66
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Vue d&#39;ensemble des donn&#233;es locales
Lorsque vous utilisez les données locales, vous ne connectez votre application à une base de données sur un serveur distinct mais à un fichier de base de données sur l'ordinateur local.  Par exemple, vous pouvez connecter une application que vous développez dans Visual Studio aux fichiers de base de données locaux suivants :  
  
-   Fichiers de base de données SQL Server Express LocalDB \(.mdf\)  
  
-   Fichiers de base de données SQL Server Express \(.mdf\)  
  
-   Fichiers de base de données Microsoft Access \(.mdb\)  
  
 Le tableau suivant fournit des liens vers les rubriques qui décrivent comment connecter votre application aux données locales :  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Procédure pas à pas : création d'un fichier de base de données local dans Visual Studio](../data-tools/create-a-sql-database-by-using-a-designer.md)|Fournit des instructions détaillées sur la création d'un fichier de base de données locale qui peut être utilisé pour tester les fonctionnalités des données et générer des applications.|  
|[Procédure pas à pas : connexion à des données dans un fichier de base de données local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)|Fournit des instructions pas à pas pour se connecter à une base de données SQL Server Express LocalDB lorsque vous créez une application Windows simple.|  
|[Procédure pas à pas : connexion à des données dans une base de données Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Fournit des instructions pas à pas de connexion à une base de données Microsoft Access.|  
|[Comment : se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Fournit des instructions pour se connecter à l'exemple de base de données Northwind dans [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)], SQL Server Compact, SQL Server Express et Access.|  
  
 Après avoir créé une source de données, puis l'avoir configurée pour accéder à un fichier de données local, vous travaillez avec les données à l'aide des mêmes technologies et des mêmes objets que si vous travailliez avec des données provenant d'autres sources.  Pour plus d'informations, consultez [Création d'applications de données](../data-tools/creating-data-applications.md).  
  
## Intégration de la base de données dans votre application  
 Si vous vous connectez aux données locales, vous pouvez non seulement vous connecter à un fichier de base de données, mais également l'intégrer dans votre application.  Par exemple, vous pouvez ouvrir le menu **Projet**, rechercher un fichier .sdf, .mdf ou .mdb existant, puis l'ajouter à votre projet.  
  
 Si vous ajoutez des fichiers de données locaux, vous créez un dataset typé et une chaîne de connexion dynamique qui pointe sur le fichier de base de données dans votre application.  Lorsque vous ajoutez un fichier de base de données à votre projet, vous utilisez l'**Assistant Configuration de source de données** pour spécifier les objets à inclure.  
  
> [!NOTE]
>  Vous pouvez configurer automatiquement votre connexion et démarrer l'**Assistant Configuration de source de données** en faisant glisser un fichier .sdf, .mdf ou .mdb de l'Explorateur de fichiers vers l'**Explorateur de solutions**.  Vous pouvez spécifier les objets à utiliser dans votre application.  
  
 Si vous utilisez l'**Assistant Configuration de source de données** pour créer la source de données pour un fichier de données local, vous êtes invité à inclure le fichier dans votre projet.  Si vous ne le faites pas, votre application contiendra uniquement la chaîne de connexion vers laquelle le chemin d'accès codé en dur pointe et pas le fichier de données réel.  Pour plus d'informations, consultez [Comment : gérer des fichiers de données locaux dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
 Une fois l'Assistant terminé, le fichier de base de données et le dataset apparaissent dans l'**Explorateur de solutions**\/l'**Explorateur de base de données** et les objets de base de données que vous avez spécifiés sont disponibles dans la fenêtre **Sources de données**.  En faisant glisser des éléments de la fenêtre **Sources de données** vers votre formulaire, vous pouvez créer des contrôles qui sont liés aux données sous\-jacentes.  Pour ouvrir la fenêtre **Sources de données**, ouvrez le menu **Données**, puis choisissez **Afficher les sources de données**.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Utilisation d'un fichier de base de données  
 Pour utiliser un fichier de base de données \(.mdf\) existant dans Visual Studio, vous devrez probablement le convertir en un fichier de base de données [!INCLUDE[sql_Denali_short](../data-tools/includes/sql_denali_short_md.md)].  Lorsque vous vous connectez à un fichier de base de données existant, un message vous demande si vous souhaitez mettre à niveau.  
  
> [!IMPORTANT]
>  Si vous mettez à niveau le fichier de base de données \(.mdf\), vous ne pouvez pas l'ouvrir dans une version antérieure de SQL Server.  
  
 Vous n'avez pas besoin de convertir le fichier de base de données \(.mdf\) si le **Nom de l'instance SQL Server** a la valeur SQLEXPRESS et que SQL Server 2008 Express est installé.  SQL Server 2008 Express est installé si Visual Studio 2010 est installé.  Pour modifier le nom de l'instance de ce fichier de base de données, ouvrez Visual Studio, ouvrez la boîte de dialogue **Ajouter une connexion**, spécifiez `.\SQLEXPRESS` comme nom de serveur, puis spécifiez la base de données ou le nom du fichier de base de données.  
  
## SQL Server Express LocalDB et SQL Server Express  
 Vous pouvez ajouter un fichier de base de données basée sur un service \(.mdf\) à tout projet dans Visual Studio.  Vous pouvez utiliser les concepteurs Visual Studio pour concevoir les tables de base de données et les autres objets de base de données et vous pouvez exécuter des requêtes.  
  
 Lorsque vous créez une base de données basée sur un service dans Visual Studio, elle utilise le moteur SQL Server Express LocalDB pour accéder au fichier de base de données \(.mdf\) alors que les versions antérieures de Visual Studio utilisaient le moteur SQL Server Express.  
  
 SQL Server Express LocalDB est la version légère de SQL Server, que vous pouvez programmer quasiment de la même façon qu'une base de données SQL Server.  SQL Server Express LocalDB s'exécute en mode utilisateur, et vous pouvez l'installer plus rapidement avec moins de composants requis et sans configuration.  
  
> [!NOTE]
>  Pour plus d'informations sur SQL Server Express LocalDB, consultez [Introducing LocalDB, an Improved SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) et [LocalDB: Where is My Database?](http://go.microsoft.com/fwlink/?LinkId=234376) sur le site Web Microsoft.  
  
 Dans Visual Studio, vous pouvez utiliser par défaut SQL Server Express au lieu de SQL Server Express LocalDB.  Dans la barre de menus, sélectionnez **Outils**, **Options**.  Sous le nœud **Outils de base de données**, choisissez **Connexions de données**.  Dans la zone de texte **Nom de l'instance SQL Server**, entrez `SQLEXPRESS`.  Sinon, vous pouvez entrer d'autres valeurs pour le nom de l'instance SQL Server \(par exemple, `SQL2008`\).  
  
 Le tableau suivant décrit les différences entre les moteurs de SQL Server Express LocalDB et de SQL Server Express.  
  
||SQL Server Express LocalDB|SQL Server Express|  
|-|--------------------------------|------------------------|  
|Type de base de données lorsque vous créez une base de données à base de service|Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] et [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], SQL Server Express LocalDB|Dans Visual Studio 2010 et les versions antérieures, SQL Server Express|  
|Nom de l'instance SQL Server dans Outils\/Options|\(LocalDB\)\\v11.0|SQLEXPRESS|  
|Valeur de la source de données dans la chaîne de connexion|\(LocalDB\)\\v11.0|.\\SQLEXPRESS|  
|Valeur de AttachDbFilename dans la chaîne de connexion|chemin\_d'accès\_fichier|chemin\_d'accès\_fichier|  
|L'instance utilisateur est requise \("User Instance\=True" dans la chaîne de connexion\)|Non|Oui|  
|Extension du fichier de base de données|.mdf|.mdf|  
  
## Avantages de SQL Server Express LocalDB  
  
-   SQL Server Express LocalDB est compatible avec les éditions service basées sur SQL Server pour les fonctionnalités que SQL Server Express LocalDB active.  Dans SQL Server, vous pouvez déplacer une base de données ou le code Transact\-SQL de SQL Server Express LocalDB dans SQL Server ou SQL Azure sans étape de mise à niveau.  Par conséquent, vous pouvez utiliser SQL Server Express LocalDB pour développer des applications qui ciblent toutes les éditions de SQL Server.  
  
-   SQL Server Express LocalDB prend en charge le même optimiseur de requête et processeur de requêtes que les éditions supérieures de SQL Server.  
  
## Chaque projet contient deux copies de la base de données  
 Lorsque vous générez un projet, le fichier de base de données peut être copié du dossier racine du projet vers le dossier de sortie \(**bin**\).  Ce comportement dépend de la propriété **Copier dans le répertoire de sortie** du fichier, et la valeur par défaut de cette propriété dépend du type de fichier de base de données que vous utilisez.  
  
 Pour afficher le dossier **bin** dans l'**Explorateur de solutions**, choisissez le bouton **Afficher tous les fichiers** dans la barre d'outils.  
  
> [!NOTE]
>  La propriété **Copier dans le répertoire de sortie** ne s'applique pas aux projets Web ou C\+\+.  
  
 Le fichier de base de données présent dans votre dossier projet racine est modifié uniquement lorsque vous modifiez le schéma ou les données de la base de données à l'aide de l'**Explorateur de serveurs**\/**Explorateur de bases de données** ou d'autres [Visual Database Tools](http://msdn.microsoft.com/fr-fr/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Lorsque vous changez des données pendant le développement d'applications, vous remplacez la base de données dans le dossier **bin**.  Par exemple, lorsque vous choisissez la touche F5 pour déboguer votre application, vous êtes connecté à la base de données qui se trouve dans ce dossier.  
  
|Valeur de la propriété **Copier dans le répertoire de sortie**|Comportement|  
|--------------------------------------------------------------------|------------------|  
|**Copier si plus récent** \(valeur par défaut pour les fichiers .sdf\)|Le fichier de base de données est copié du répertoire du projet dans le répertoire **bin** lors de la première génération du projet.  La propriété **Date de modification** des fichiers fait l'objet d'une comparaison chaque fois que vous régénérez le projet.  Si le fichier figurant dans le dossier de projet est plus récent, il est copié dans le dossier **bin** et remplace le fichier précédent.  Sinon, aucun fichier n'est copié. **Caution:**  Nous ne recommandons pas cette valeur pour les fichiers .mdb ou .mdf.  Le fichier de base de données peut changer même si les données ne sont pas modifiées.  Le fichier peut être marqué comme récent si vous ouvrez simplement une connexion \(par exemple, si vous développez le nœud **Tables** dans l'**Explorateur de serveurs**\).|  
|**Toujours copier** \(valeur par défaut pour les fichiers .mdf et .mdb\)|Le fichier de base de données est copié du répertoire de projet vers le répertoire **bin** chaque fois que vous générez votre application.  Toute modification apportée au fichier de données dans le dossier de sortie est remplacée lors de la prochaine exécution de l'application.|  
|**Ne pas copier**|Le système ne remplace pas le fichier dans le répertoire **Bin**.  Votre application crée une chaîne de connexion dynamique qui pointe sur le fichier de base de données du répertoire de sortie.  Par conséquent, vous devez copier manuellement le fichier dans le répertoire de sortie pour que les données du répertoire de sortie correspondent aux données du répertoire du projet.|  
  
## Problèmes courants liés aux données locales  
 Le tableau suivant explique les problèmes courants que vous pouvez rencontrer lorsque vous travaillez avec des fichiers de données locaux.  
  
|Problème|Explication|  
|--------------|-----------------|  
|Chaque fois que je teste mon application et que je modifie les données, mes modifications ont disparu au lancement suivant de l'application.|La valeur de la propriété **Copier dans le répertoire de sortie** est **Copier si plus récent** ou **Toujours copier**.  La base de données présente dans votre dossier de sortie \(la base de données qui est modifiée lorsque vous testez votre application\) est remplacée chaque fois que vous générez votre projet.  Pour plus d'informations, consultez [Comment : gérer des fichiers de données locaux dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Un message apparaît indiquant que le fichier de données est verrouillé.|Access \(fichiers .mdb\) : vérifiez que le fichier n'est pas ouvert dans un autre programme, par exemple Access.<br /><br /> SQL Server Express \(fichiers .mdf\) : SQL Express verrouille le fichier de données si vous tentez de le copier, de le déplacer ou de le renommer hors de l'IDE de Visual Studio.|  
|L'accès est refusé lorsque plusieurs utilisateurs essaient d'accéder simultanément à la même base de données.|Visual Studio tire parti des *instances d'utilisateur*, qui est une fonctionnalité de SQL Server Express qui crée une instance séparée de SQL Server pour chaque utilisateur.  Lorsqu'un utilisateur accède au fichier, aucun autre utilisateur ne peut s'y connecter.  Ce problème peut se produire si, par exemple, vous essayez d'exécuter une application Web simultanément sur un serveur de développement ASP.NET et dans IIS \(Internet Information Services\), car IIS s'exécute en général sous un compte différent.|  
  
## Voir aussi  
 [Procédure pas à pas : connexion à des données dans un fichier de base de données local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [Procédure pas à pas : connexion à des données dans une base de données Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)