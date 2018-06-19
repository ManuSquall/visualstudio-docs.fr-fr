---
title: 'Comment : spécifier où Visual Studio copie les fichiers | Documents Microsoft'
ms.custom: ''
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
ms.openlocfilehash: 2b4e626253d9d07a9f263304d02739bdb3f4b012
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557890"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Comment : spécifier l'endroit où Visual Studio copie les fichiers
Quand vous publiez une application à l'aide de ClickOnce, la propriété `Publish Location` indique l'emplacement de destination des fichiers d'application et du manifeste. Il peut s’agir d’un chemin d’accès de fichier ou du chemin d’accès à un serveur FTP.  
  
 Vous pouvez spécifier le `Publish Location` propriété sur le **publier** page de la **Concepteur de projet**, ou à l’aide de l’Assistant Publication. Pour plus d’informations, consultez [Comment : publier une Application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
> [!NOTE]
>  Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d'éviter la présence de dossiers de la version précédente dans le répertoire d'installation.  
  
### <a name="to-specify-a-publishing-location"></a>Pour spécifier un emplacement de publication  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans le **Publish Location** , entrez l’emplacement de publication à l’aide d’un des formats suivants :  
  
    -   Pour publier sur un chemin de partage ou le disque du fichier, entrez le chemin d’accès à l’aide d’un chemin d’accès UNC (\\\Server\ApplicationName) ou un chemin d’accès de fichier (C:\Deploy\ApplicationName).  
  
    -   Pour publier vers un serveur FTP, entrez le chemin d’accès dans le format suivant : ftp://ftp.microsoft.com/Nom_application.  
  
     Notez que le texte doit être présent dans le **l’emplacement de publication** zone afin que le bouton de navigation (**...** ) bouton fonctionne.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)