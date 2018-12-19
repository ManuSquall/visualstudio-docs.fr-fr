---
title: Indiquez où copier les fichiers | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4154f7b3a148968347b39911b9a7e9c28830eac
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068313"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Procédure : spécifier l’endroit où Visual Studio copie les fichiers
Quand vous publiez une application à l'aide de ClickOnce, la propriété `Publish Location` indique l'emplacement de destination des fichiers d'application et du manifeste. Il peut s’agir d’un chemin d’accès de fichier ou du chemin d’accès à un serveur FTP.  
  
 Vous pouvez spécifier la propriété `Publish Location` dans la page **Publier** du **Concepteur de projets** ou en utilisant l’Assistant Publication. Pour plus d'informations, voir [Procédure : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.  
  
### <a name="to-specify-a-publishing-location"></a>Pour spécifier un emplacement de publication  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l’onglet **Publier**.  
  
3. Dans le champ **Emplacement de publication**, entrez l’emplacement de publication dans l’un des formats suivants :  
  
   - Pour publier vers un partage de fichiers ou un chemin de disque, entrez le chemin sous forme de chemin UNC (*\\\Serveur\Nom_application*) ou de chemin de fichier (*C:\Déploiement\Nom_application*).  
  
   - Pour publier vers un serveur FTP, entrez le chemin dans le format suivant : <em>ftp://ftp.microsoft.com/\<Nom_application></em>.  
  
     Notez que du texte doit figurer dans la zone **Emplacement de publication** pour que le bouton Parcourir (**...**) fonctionne.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)