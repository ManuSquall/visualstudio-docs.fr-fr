---
title: Vue d’ensemble des données locales | Microsoft Docs
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
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b2bd594ba017a07ad3886a9aeb4b59d6f479a708
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501024"
---
# <a name="local-data-overview"></a>Vue d'ensemble des données locales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous développez des applications de données, il est généralement préférable d’utiliser une copie locale d’une base de données, afin que vous n’introduisez pas d’erreurs dans les données de production. Même partage une base de données de test avec d’autres développeurs crée des problèmes potentiels si deux développeurs d’introduire des erreurs qui interagissent de manières difficiles à détecter. Vous pouvez éviter tous ces pièges à l’aide de vos propres données de test sur votre ordinateur local. La plupart si pas tous les systèmes de base de données permettre de créer des fichiers de données locaux. Pour les projets .NET, Visual Studio fournit la prise en charge spéciale pour les fichiers de base de données locales SQL Server (.mdf) et les fichiers de base de données Microsoft Access (.mdb).  
  
 Visual Studio prend en charge ces scénarios :  
  
1.  
  
2.  
  
-  
  
-  
  
-   Créer un projet de base de données SQL Server en cliquant sur le nœud solution dans l’Explorateur de solutions et en choisissant **ajouter &#124; nouveau projet**.  Dans le volet gauche, choisissez **SQL Server &#124; base de données** projet puis cliquez sur OK. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud de projet de base de données pour importer un fichier de base de données locale, puis développer l’application qui se connecte à la base de données produite par le projet. Utile lors du développement et de la modification du schéma de base de données en même temps que vous développez l’application.  
  
     ![Importer la base de données dans le projet de base de données](../data-tools/media/raddata-import-database-into-database-project.png "raddata Importer base de données dans le projet de base de données")  
  
-   Si vous créez une nouvelle base de données, vous devez tout d’abord ajouter un **fichier de base de données basée sur le Service** à votre projet (**projet &#124; ajouter un nouvel élément)**. Cette opération crée un nouveau fichier .mdf est attaché à l’instance de SQL Server par défaut sur l’ordinateur local, c'est-à-dire par défaut (localdb) \MSSQLocalDB. La base de données doit apparaître dans l’Explorateur de serveurs. Développez le nœud et avec le bouton droit sur les nœuds à ajouter de nouveaux objets de base de données tels que des tables, vues, fonctions et ainsi de suite.  
  
 Pour plus d’informations sur SQL Server Express LocalDB, consultez [Introducing LocalDB, an Improved SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) et [LocalDB : Where is My Database ?](http://go.microsoft.com/fwlink/?LinkId=234376) sur le site Web Microsoft.  
  
 Le tableau suivant fournit des liens vers les rubriques qui décrivent comment connecter votre application aux données locales :  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Créer une base de données SQL à l’aide d’un concepteur](../data-tools/create-a-sql-database-by-using-a-designer.md)|Fournit des instructions détaillées sur la création d’un fichier de base de données locale qui peut être utilisé pour tester les fonctionnalités des données et générer des applications.|  
|[Procédure pas à pas : connexion à des données dans un fichier de base de données local (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Fournit des instructions pas à pas pour se connecter à une base de données SQL Server Express LocalDB lorsque vous créez une application Windows simple.|  
|[Se connecter à des données dans une base de données Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Fournit des instructions pas à pas de connexion à une base de données Microsoft Access.|  
|[Guide pratique pour se connecter à la base de données Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Fournit des instructions pour se connecter à l'exemple de base de données Northwind dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express et Access.|  
  
## <a name="use-the-connection-string"></a>Utiliser la chaîne de connexion  
 Ceci est l’approche la plus simple et constitue un bon choix lorsque votre application lit uniquement à partir de la base de données et lors de l’utilisation de bases de données par des tiers. Le fichier de base de données peut être placée n’importe où sur l’ordinateur local que votre application est autorisé à accéder, et que le système de base de données prend en charge.  
  
1.  (Facultatif) Créez une nouvelle connexion, comme décrit dans [ajouter de nouvelles connexions](../data-tools/add-new-connections.md). Pour les bases de données tierces et les fichiers .mdf pour lequel vous déjà connaître la chaîne de connexion et ne sera pas effectuer de liaison de données ou à l’aide d’une source de données telles que les classes Entity Framework ou les jeux de données, cette étape n’est pas nécessaire. Utilisez simplement la chaîne de connexion pour se connecter au fichier local. Pour les fichiers .mdf, consultez [mettre à niveau les fichiers .mdf](../data-tools/upgrade-dot-mdf-files.md) et [l’établissement de la connexion](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (Facultatif) Si vous utilisez des jeux de données Entity Framework ou LINQ to SQL, vous devez ensuite créer la source de données à l’aide de l’Assistant de Configuration de Source de données. Pour plus d’informations, consultez [Ajouter de nouvelles sources de données](../data-tools/add-new-data-sources.md).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Ajouter un .mdf existant à votre projet  
 Si votre application sera insertion, suppression ou la mise à jour des données et que vous souhaitez conserver une copie du fichier d’origine disponible, envisagez d’ajouter le fichier à votre projet. Lorsque vous procédez ainsi, vous pouvez définir la propriété d’élément dessus pour **Copy to Output Directory** à **toujours copier** ou **Copier si plus récent**et de développer l’application. Chaque fois que vous générez l’application, la base de données d’origine est copié dans le dossier de sortie et les modifications de votre application sont effectuées sur la copie. De cette façon, que vous avez toujours une nouvelle copie des données d’origine.  
  
1.  Utilisez **Explorateur de fichiers Windows** faire glisser et déposer le fichier .mdf à partir de son emplacement actuel sur le nœud du projet dans l’Explorateur de solutions dans Visual Studio.  Si le fichier est déjà attaché à une instance de base de données locale, vous devez tout d’abord le détacher. Une fois que vous le placez dans le projet, Visual Studio sera automatiquement l’attacher à l’instance de base de données locale par défaut.  
  
2.  Avec le bouton droit sur le nouveau nœud de base de données et choisissez Propriétés. Sélectionnez le comportement de copie, à savoir **toujours copier** ou **Copier si plus récent**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Créer un projet de base de données SQL Server et importer votre base de données  
 Il s’agit d’une bonne option lorsque vous développerez la base de données elle-même, peut-être ajouter des colonnes ou tables, ou la modification des types de données.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Chaque projet contient deux copies de la base de données  
 Lorsque vous générez un projet, le fichier de base de données peut être copié à partir du dossier racine du projet dans la sortie, **bin**, dossier. Ce comportement varie selon le **Copy to Output Directory** propriété du fichier et la valeur par défaut de cette propriété varient selon le type de fichier de base de données que vous utilisez.  
  
 Pour afficher le **bin** dossier **l’Explorateur de solutions**, choisissez le **afficher tous les fichiers** dans la barre d’outils.  
  
> [!NOTE]
>  Le **Copy to Output Directory** propriété ne s’applique pas aux projets web ou C++.  
  
 Le fichier de base de données dans votre dossier projet racine est modifié uniquement lorsque vous modifiez le schéma de base de données ou les données à l’aide de **Explorateur de serveurs**/**Database Explorer** ou autres [Visual Outils de base de données](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Lorsque vous modifiez des données pendant le développement d’application, vous modifiez la base de données dans le **bin** dossier. Par exemple, lorsque vous choisissez la touche F5 pour déboguer votre application, vous êtes connecté à la base de données qui se trouve dans ce dossier.  
  
|Valeur de **Copy to Output Directory** propriété|Comportement|  
|----------------------------------------------------|--------------|  
|**Copier si plus récent** (valeur par défaut pour les fichiers .sdf)|Le fichier de base de données est copié à partir du répertoire de projet pour le **bin** directory la première fois que vous générez le projet. Le **Date de modification** propriété des fichiers est ensuite comparée chaque fois que vous générez le projet à nouveau. Si le fichier dans le dossier du projet est plus récent, il est copié dans le **bin** dossier, en remplaçant le fichier précédent. Sinon, aucun fichier n'est copié. **Attention :** nous ne recommandons pas cette valeur pour les fichiers .mdb ou .mdf. Le fichier de base de données peut changer même si les données ne sont pas modifiées. Le fichier peut être marqué comme récent si vous ouvrez simplement une connexion (par exemple, développez le **Tables** nœud **Explorateur de serveurs**).|  
|**Toujours copier** (valeur par défaut pour les fichiers .mdf et .mdb)|Le fichier de base de données est copié à partir du répertoire de projet pour le **bin** directory chaque fois que vous générez votre application. Toute modification apportée au fichier de données dans le dossier de sortie est remplacée lors de la prochaine exécution de l’application.|  
|**Ne pas copier**|Le système ne remplace pas le fichier dans le **bin** directory. Votre application crée une chaîne de connexion dynamique qui pointe sur le fichier de base de données du répertoire de sortie. Par conséquent, vous devez copier manuellement le fichier dans le répertoire de sortie pour que les données du répertoire de sortie correspondent aux données du répertoire du projet.|  
  
## <a name="common-issues-with-local-data"></a>Problèmes courants liés aux données locales  
 Le tableau suivant explique les problèmes courants que vous pouvez rencontrer lorsque vous travaillez avec des fichiers de données locaux.  
  
|Problème|Explication|  
|-----------|-----------------|  
|Chaque fois que je teste mon application et que je modifie les données, mes modifications ont disparu au lancement suivant de l'application.|La valeur de la **Copy to Output Directory** propriété est **Copier si plus récent** ou **toujours copier**. La base de données présente dans votre dossier de sortie (la base de données qui est modifiée lorsque vous testez votre application) est remplacée chaque fois que vous générez votre projet. Pour plus d’informations, consultez [Comment : gérer les fichiers de données Local dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Un message apparaît indiquant que le fichier de données est verrouillé.|Access (fichiers .mdb) : vérifiez que le fichier n'est pas ouvert dans un autre programme, par exemple Access.<br /><br /> SQL Server Express (fichiers .mdf) : SQL Express verrouille le fichier de données si vous tentez de le copier, de le déplacer ou de le renommer hors de l'IDE de Visual Studio.|  
|L'accès est refusé lorsque plusieurs utilisateurs essaient d'accéder simultanément à la même base de données.|Visual Studio tire parti de *instances utilisateur*, qui est une fonctionnalité de SQL Server Express qui crée une instance distincte de SQL Server pour chaque utilisateur. Lorsqu'un utilisateur accède au fichier, aucun autre utilisateur ne peut s'y connecter. Ce problème peut se produire si, par exemple, vous essayez d'exécuter une application Web simultanément sur un serveur de développement ASP.NET et dans IIS (Internet Information Services), car IIS s'exécute en général sous un compte différent.|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Connexion aux données dans un fichier de base de données locale (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Se connecter à des données dans une base de données Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)