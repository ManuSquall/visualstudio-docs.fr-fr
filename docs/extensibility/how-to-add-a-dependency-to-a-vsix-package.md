---
title: "Comment : ajouter une dépendance à un Package VSIX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 27fbf8c079ca1270074d7cae683ef6f8127e2a5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Comment : ajouter une dépendance à un Package VSIX

Vous pouvez configurer un déploiement de package VSIX qui installe les dépendances qui ne sont pas déjà présents sur l’ordinateur cible. Pour ce faire, inclure les dépendances VSIX dans le fichier source.extension.vsixmanifest.

## <a name="to-add-a-dependency"></a>Pour ajouter une dépendance

1. Ouvrez le fichier source.extension.vsixmanifest dans le **conception** vue. Accédez à la **dépendances** onglet et cliquez sur **nouveau**.

2. Pour ajouter une extension installée : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **extension installée** , puis, pour le **nom**, sélectionnez une extension dans la liste.

3. Pour ajouter une autre extension VSIX qui n’est pas installé : : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **fichier sur le système de fichiers** , puis utilisez le **Parcourir** pour sélectionner l’extension VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Nécessite une version spécifique de Visual Studio

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, elle dépend d’une fonctionnalité intégrée à 15.3, vous pouvez spécifier le numéro de build dans votre projet VSIX **le InstallationTarget**. Par exemple, release 15.3 a un numéro de build de '15.0.26730.3'. Vous pouvez voir le mappage des versions à des numéros de build [ici](../install/visual-studio-build-numbers-and-release-dates.md). Notez que l’aide du numéro de version '15.3' ne fonctionnera pas correctement.

Si votre extension requiert 15.3 ou une version ultérieure, vous déclarez le **le InstallationTarget Version** comme [15.0.26730.3, 16.0) :

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Le VSIXInstaller détecte les versions antérieures de Visual Studio et informer l’utilisateur qu’une mise à jour ultérieure est nécessaire.


## <a name="see-also"></a>Voir aussi

 [Référence de schéma 1.0 Extension VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md) [préparation des Extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)