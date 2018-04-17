---
title: L’utilisation de fichiers de base de données locale dans la vue d’ensemble des Solutions Office | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a171fe12a1476e19c46f0aef704342de375c7865
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Vue d'ensemble de l'utilisation de fichiers de base de données locaux dans les solutions Office
  Vous pouvez inclure un fichier de base de données, comme un fichier SQL Server Express (.mdf) ou un fichier Microsoft Office Access (.mdb), dans votre solution Office. Cela permet aux utilisateurs finaux de gérer une base de données local dans les situations où le maintien d’une base de données centralisée n’est pas nécessaire, par exemple dans une solution de stock locale qui est utilisée sur un seul ordinateur.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>Importation du fichier de base de données dans un projet  
 Pour importer le fichier de base de données dans votre projet, utilisez le **Assistant de Configuration de Source de données** pour créer une source de données basée sur le fichier de base de données. L’Assistant ajoute le fichier de base de données et un dataset typé à votre projet.  
  
## <a name="deploying-the-database-file"></a>Déploiement du fichier de base de données  
 Le **Assistant de Configuration de Source de données** utilise un chemin d’accès relatif pour créer des connexions dans le fichier de base de données locale. Cela vous permet de copier la solution d’un ordinateur à un autre si vous conservez les positions relatives des fichiers.  
  
 Si vous déployez votre solution sur un serveur et distribuez ensuite le document à chaque utilisateur final, vous devez également distribuer le fichier de base de données et l’installer à la même position par rapport au document. Cela signifie que l’utilisateur final ne peut pas déplacer le document vers un nouvel emplacement sur l’ordinateur, sauf si elle se déplace également le fichier de base de données.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Les fichiers de base de données locale et la mise en cache le jeu de données  
 Dans les solutions au niveau du document pour Microsoft Office Excel et Microsoft Office Word, vous pouvez mettre en cache des groupes de données dans le document en marquant l’instance du jeu de données avec l’attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Lorsque vous ajoutez le fichier de base de données à votre projet à l’aide de la **Assistant de Configuration de Source de données**, un dataset typé est automatiquement ajouté à votre projet. Il est rarement nécessaire d’appliquer <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> à ce jeu de données, car les données sont déjà locales sur l’ordinateur. Pour plus d'informations, consultez [Caching Data](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données aux contrôles dans les Solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Comment : remplir des Documents avec les données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : mettre à jour une Source de données avec des données à partir d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Mise en cache des données](../vsto/caching-data.md)  
  
  