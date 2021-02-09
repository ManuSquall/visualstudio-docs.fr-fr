---
title: Spécifier l’emplacement de copie des fichiers | Microsoft Docs
description: Découvrez comment définir la propriété emplacement de publication pour une application ClickOnce, qui spécifie l’emplacement où sont placés les fichiers et le manifeste de l’application.
ms.custom:
- SEO-VS-2020
- seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50f3e5d8500e57dd336919a5da58af094db97169
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887417"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Guide pratique pour spécifier l’endroit où Visual Studio copie les fichiers
Quand vous publiez une application à l'aide de ClickOnce, la propriété `Publish Location` indique l'emplacement de destination des fichiers d'application et du manifeste. Il peut s'agir d'un chemin d'accès de fichier ou du chemin d'accès à un serveur FTP.

 Vous pouvez spécifier la propriété `Publish Location` dans la page **Publier** du **Concepteur de projets** ou en utilisant l’Assistant Publication. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.

### <a name="to-specify-a-publishing-location"></a>Pour spécifier un emplacement de publication

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Dans le champ **Emplacement de publication**, entrez l’emplacement de publication dans l’un des formats suivants :

   - Pour publier sur un partage de fichiers ou un chemin d’accès de disque, entrez le chemin d’accès UNC (*\\ \Server\ApplicationName*) ou un chemin d’accès de fichier (*C:\Deploy\ApplicationName*).

   - Pour publier sur un serveur FTP, entrez le chemin d’accès au <em>format \<ApplicationName> ftp://ftp.Microsoft.com/</em>.

     Notez que le texte doit être présent dans la zone **emplacement de publication** pour que le bouton de navigation (**...**) fonctionne.

## <a name="see-also"></a>Voir aussi
- [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)