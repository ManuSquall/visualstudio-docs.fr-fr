---
title: 'Comment : créer des Associations de fichiers pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15d9b81bd342ccd8a5ee3377323e140ab1167c10
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633042"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Guide pratique pour créer des associations de fichiers pour une application ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications peuvent être associées à une ou plusieurs extensions de nom de fichier afin que l’application démarrera automatiquement quand l’utilisateur ouvre un fichier de ces types. Ajout du support d’extension de nom de fichier à un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est simple.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Pour créer des associations de fichiers pour une application ClickOnce

1. Créer un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application normalement, ou utilisez votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

2. Ouvrez le manifeste d’application avec un texte ou un éditeur XML, tel que le bloc-notes.

3. Recherchez l’élément `assembly` . Pour plus d’informations, consultez [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md).

4. En tant qu’enfant de le `assembly` élément, ajoutez un `fileAssociation` élément. Le `fileAssociation` élément présente quatre attributs :

   - `extension`: L’extension de nom de fichier à associer avec l’application.

   - `description`: Description du type de fichier, qui apparaîtra dans l’interpréteur de commandes Windows.

   - `progid`: Chaîne identifiant de manière unique le type de fichier pour le marquer dans le Registre.

   - `defaultIcon`: Une icône à utiliser pour ce type de fichier. L’icône doit être ajoutée comme une ressource de fichier dans le manifeste d’application. Pour plus d'informations, consultez [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Pour obtenir un exemple de la `file` et `fileAssociation` éléments, consultez [ \<fileAssociation > élément](../deployment/fileassociation-element-clickonce-application.md).

5. Si vous souhaitez associer plusieurs types de fichier à l’application, ajoutez d’autres `fileAssociation` éléments. Notez que le `progid` attribut doit être différent pour chacun.

6. Une fois que vous avez terminé avec le manifeste d’application, signer à nouveau le manifeste. Cela aide à partir de la ligne de commande *Mage.exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Pour plus d’informations, consultez [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Voir aussi
- [\<fileAssociation > élément](../deployment/fileassociation-element-clickonce-application.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)