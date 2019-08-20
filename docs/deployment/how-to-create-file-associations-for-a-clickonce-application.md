---
title: 'Procédure : Créer des associations de fichiers pour une application ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 0526351d2b3e2c223aacbe0e58d9ee39bd1b19c4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924557"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procédure : Créer des associations de fichiers pour une application ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]les applications peuvent être associées à une ou plusieurs extensions de nom de fichier, afin que l’application démarre automatiquement lorsque l’utilisateur ouvre un fichier de ces types. L’ajout de la prise en charge [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de l’extension de nom de fichier à une application est simple.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Pour créer des associations de fichiers pour une application ClickOnce

1. Créez une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application normalement, ou utilisez votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] existante.

2. Ouvrez le manifeste de l’application à l’aide d’un éditeur de texte ou XML, tel que le bloc-notes.

3. Recherchez l’élément `assembly` . Pour plus d’informations, consultez [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md).

4. En tant qu’enfant de `assembly` l’élément, ajoutez `fileAssociation` un élément. L' `fileAssociation` élément a quatre attributs:

   - `extension`: Extension de nom de fichier que vous souhaitez associer à l’application.

   - `description`: Description du type de fichier, qui apparaîtra dans le shell Windows.

   - `progid`: Chaîne identifiant de façon unique le type de fichier, pour le marquer dans le registre.

   - `defaultIcon`: Icône à utiliser pour ce type de fichier. L’icône doit être ajoutée en tant que ressource de fichier dans le manifeste de l’application. Pour plus d’informations, consultez [Guide pratique pour Inclure un fichier de données dans une application ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Pour obtenir un exemple des `file` éléments `fileAssociation` et, consultez [ \<FileAssociation >, élément](../deployment/fileassociation-element-clickonce-application.md).

5. Si vous souhaitez associer plus d’un type de fichier à l’application, ajoutez des `fileAssociation` éléments supplémentaires. Notez que l' `progid` attribut doit être différent pour chaque.

6. Une fois que vous avez fini d’utiliser le manifeste d’application, resignez le manifeste. Vous pouvez effectuer cette opération à partir de la ligne de commande à l’aide de *Mage. exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Pour plus d’informations, consultez [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Voir aussi
- [\<fileAssociation >, élément](../deployment/fileassociation-element-clickonce-application.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)