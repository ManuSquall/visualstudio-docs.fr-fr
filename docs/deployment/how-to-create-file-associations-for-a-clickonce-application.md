---
title: 'Comment : créer des Associations de fichiers pour une Application ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 75215164de3aedfe1ea0168275280304dfd5def9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Comment : créer des associations de fichiers pour une application ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications peuvent être associées à une ou plusieurs extensions de nom de fichier afin que l’application sera démarrée automatiquement lorsque l’utilisateur ouvre un fichier de ces types. Ajout du support d’extension de nom de fichier à un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est simple.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Pour créer des associations de fichiers pour une application ClickOnce  
  
1.  Créer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application normalement, ou utiliser votre existante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
2.  Ouvrez le manifeste d’application avec un texte ou un éditeur XML, tel que le bloc-notes.  
  
3.  Recherchez l'élément `assembly`. Pour plus d’informations, consultez [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  En tant qu’enfant de la `assembly` élément, ajouter un `fileAssociation` élément. Le `fileAssociation` élément présente quatre attributs :  
  
    -   `extension`: L’extension de nom de fichier à associer avec l’application.  
  
    -   `description`: Description du type de fichier, qui apparaîtra dans le shell Windows.  
  
    -   `progid`: Chaîne identifiant de manière unique le type de fichier pour le marquer dans le Registre.  
  
    -   `defaultIcon`: Une icône à utiliser pour ce type de fichier. L’icône doit être ajouté comme une ressource de fichier dans le manifeste d’application. Pour plus d'informations, consultez [Comment : inclure un fichier de données dans une application ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Pour obtenir un exemple de la `file` et `fileAssociation` éléments, consultez [ \<fileAssociation > élément](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Si vous souhaitez associer plusieurs types de fichier à l’application, ajouter d’autres `fileAssociation` éléments. Notez que le `progid` attribut doit être différent pour chacun.  
  
6.  Une fois que vous avez terminé avec le manifeste d’application, signer de nouveau le manifeste. Faire cela à partir de la ligne de commande à l’aide de Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Pour plus d’informations, consultez [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Voir aussi  
 [\<fileAssociation > élément](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifeste d’Application ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)