---
title: 'Comment : Ajouter une dépendance à un forfait VSIX Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711080"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Comment : Ajouter une dépendance à un forfait VSIX

Vous pouvez configurer un déploiement de colis VSIX qui installe toutes les dépendances qui ne sont pas déjà présentes sur l’ordinateur cible. Pour ce faire, inclure les dépendances VSIX au fichier *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Pour ajouter une dépendance

1. Ouvrez le fichier *source.extension.vsixmanifest* dans la vue **Design.** Rendez-vous à l’onglet **Dépendances** et cliquez sur **Nouveau**.

2. Pour ajouter une extension installée : dans la boîte de dialogue **Add New Dependency,** sélectionnez **l’extension installée,** puis, pour le **nom,** sélectionnez une extension sur la liste.

3. Pour ajouter un autre VSIX qui n’est pas installé : dans la boîte de dialogue **Add New Dependency,** sélectionnez Fichier sur le **système de fichiers,** puis utilisez le bouton **Parcourir** pour sélectionner le VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Nécessitez une version spécifique de Visual Studio

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, cela dépend d’une fonctionnalité sortie en 15.3, vous pouvez spécifier le numéro de build dans votre **installation VSIXTarget**. Par exemple, la version 15.3 a un nombre de build de '15.0.26730.3'. Vous pouvez voir la cartographie des versions pour construire des nombres [ici](../install/visual-studio-build-numbers-and-release-dates.md). Notez que l’utilisation du numéro de version '15.3' ne fonctionnera pas correctement.

Si votre extension nécessite 15,3 ou plus, vous déclareriez la **version InstallationTarget** comme [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Le VSIXInstaller détectera les versions antérieures de Visual Studio et informera l’utilisateur qu’une mise à jour ultérieure est nécessaire.

## <a name="see-also"></a>Voir aussi

- [SCHÉMA d’extension VSIX 1.0 référence](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomie d’un paquet VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Préparer les extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
