---
title: Vue d’ensemble de l’utilisation des fichiers de base de données locaux dans les solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea260a6286c8a923d56ab7a5088b55de57004489
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982243"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Vue d’ensemble de l’utilisation des fichiers de base de données locaux dans les solutions Office
  Vous pouvez inclure un fichier de base de données, tel qu’un fichier SQL Server Express (*. mdf*) ou un fichier d’accès Microsoft Office (*. mdb*), dans votre solution Office. Cela permet aux utilisateurs finaux de conserver une base de données locale dans les situations où la maintenance d’une base de données centralisée n’est pas requise, par exemple dans une solution d’inventaire local qui est utilisée sur un seul ordinateur.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importer le fichier de base de données dans un projet
 Pour importer le fichier de base de données dans votre projet, utilisez l' **Assistant Configuration de source de données** pour créer une source de données basée sur le fichier de base de données. L’Assistant ajoute le fichier de base de données et un DataSet typé à votre projet.

## <a name="deploy-the-database-file"></a>Déployer le fichier de base de données
 L' **Assistant Configuration de source de données** utilise un chemin d’accès relatif pour créer des connexions au fichier de base de données local. Cela vous permet de copier la solution d’un ordinateur à un autre si vous conservez les positions relatives des fichiers.

 Si vous déployez votre solution sur un serveur, puis distribuez le document à chaque utilisateur final, vous devez également distribuer manuellement le fichier de base de données et l’installer à la même position relative au document. Cela signifie que l’utilisateur final ne peut pas déplacer le document vers un nouvel emplacement sur son ordinateur, à moins qu’il ne déplace également le fichier de base de données.

## <a name="local-database-files-and-caching-the-dataset"></a>Fichiers de base de données locaux et mise en cache du jeu de données
 Dans les solutions au niveau du document pour Microsoft Office Excel et Microsoft Office Word, vous pouvez mettre en cache des jeux de données dans le document en marquant l’instance de DataSet avec l’attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Lorsque vous ajoutez le fichier de base de données à votre projet à l’aide de l' **Assistant Configuration de source de données**, un DataSet typé est automatiquement ajouté à votre projet. Il est rarement nécessaire d’appliquer <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> à ce jeu de données, car les données sont déjà locales sur l’ordinateur de l’utilisateur. Pour plus d’informations, consultez mettre [en cache les données](../vsto/caching-data.md).

## <a name="see-also"></a>Voir aussi
- [Lier des données à des contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Comment : remplir des documents avec des données d’une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Comment : mettre à jour une source de données avec les données d’un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Données de cache](../vsto/caching-data.md)
