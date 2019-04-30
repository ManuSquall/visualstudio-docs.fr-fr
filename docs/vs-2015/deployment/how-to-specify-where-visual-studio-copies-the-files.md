---
title: 'Procédure : Spécifiez où Visual Studio 2015 copie les fichiers | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d36c5dafa37673263ab13dc46c7f02e44448fd8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441613"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procédure : Spécifier l’emplacement où Visual Studio copie les fichiers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous publiez une application à l'aide de ClickOnce, la propriété `Publish Location` indique l'emplacement de destination des fichiers d'application et du manifeste. Il peut s'agir d'un chemin d'accès de fichier ou du chemin d'accès à un serveur FTP.

 Vous pouvez spécifier la propriété `Publish Location` dans la page **Publier** du **Concepteur de projets** ou en utilisant l’Assistant Publication. Pour plus d'informations, voir [Procédure : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.

### <a name="to-specify-a-publishing-location"></a>Pour spécifier un emplacement de publication

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Publier**.

3. Dans le champ **Emplacement de publication**, entrez l’emplacement de publication dans l’un des formats suivants :

   - Pour publier vers un chemin de partage ou le disque du fichier, entrez le chemin d’accès à l’aide d’un chemin d’accès UNC (\\\Server\ApplicationName) ou un chemin d’accès de fichier (C:\Deploy\ApplicationName).

   - Pour publier vers un serveur FTP, entrez le chemin d’accès dans le format suivant : ftp://ftp.microsoft.com/Nom_application.

     Notez que du texte doit figurer dans la zone **Emplacement de publication** pour que le bouton Parcourir (**...**) fonctionne.

## <a name="see-also"></a>Voir aussi
 [Publier des Applications ClickOnce](../deployment/publishing-clickonce-applications.md) [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
