---
title: 'Procédure : Ajouter une dépendance à un Package VSIX | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1aabb7feaa565f5118904bba3850b153a20445b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911779"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procédure : Ajouter une dépendance à un package VSIX

Vous pouvez configurer un déploiement de package VSIX qui installe les dépendances qui ne sont pas déjà présents sur l’ordinateur cible. Pour ce faire, inclure les dépendances VSIX pour le *source.extension.vsixmanifest* fichier.

## <a name="to-add-a-dependency"></a>Pour ajouter une dépendance

1. Ouvrez le *source.extension.vsixmanifest* de fichiers dans le **conception** vue. Accédez à la **dépendances** onglet et cliquez sur **New**.

2. Pour ajouter une extension installée : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **installé extension** , puis, pour le **nom**, sélectionnez une extension dans la liste.

3. Pour ajouter une autre extension VSIX qui n’est pas installé : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **fichier sur le système de fichiers** , puis utilisez le **Parcourir** bouton pour sélectionner l’extension VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Exiger une version spécifique de Visual Studio

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, elle dépend d’une fonctionnalité introduite dans la version 15.3, vous pouvez spécifier le numéro de build dans votre projet VSIX **le InstallationTarget**. Par exemple, la version 15.3 a un numéro de build de '15.0.26730.3'. Vous pouvez voir le mappage des versions pour les numéros de build [ici](../install/visual-studio-build-numbers-and-release-dates.md). Notez que l’utilisation du numéro de la version '15.3' ne fonctionnera pas correctement.

Si votre extension requiert 15.3 ou version ultérieure, vous déclarez le **le InstallationTarget Version** comme [15.0.26730.3, 16.0) :

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Le VSIXInstaller détecte les versions antérieures de Visual Studio et informer l’utilisateur qu’une mise à jour ultérieure est nécessaire.

## <a name="see-also"></a>Voir aussi

- [Référence du schéma 1.0 extension VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Préparer des extensions pour le déploiement Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
