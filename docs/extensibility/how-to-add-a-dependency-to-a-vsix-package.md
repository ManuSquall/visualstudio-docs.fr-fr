---
title: 'Comment : ajouter une dépendance à un package VSIX | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b7ee7cbc4dee800351689386056389d274e07f4f
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012228"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Comment : ajouter une dépendance à un package VSIX

Vous pouvez configurer un déploiement de package VSIX qui installe toutes les dépendances qui ne sont pas déjà présentes sur l’ordinateur cible. Pour ce faire, incluez les dépendances VSIX dans le fichier *source. extension. vsixmanifest* .

## <a name="to-add-a-dependency"></a>Pour ajouter une dépendance

1. Ouvrez le fichier *source. extension. vsixmanifest* en mode **Design** . Accédez à l’onglet **dépendances** , puis cliquez sur **nouveau**.

2. Pour ajouter une extension installée : dans la boîte de dialogue **Ajouter une nouvelle dépendance** , sélectionnez **extension installée** , puis, pour le **nom**, sélectionnez une extension dans la liste.

3. Pour ajouter un autre VSIX qui n’est pas installé : dans la boîte de dialogue **Ajouter une nouvelle dépendance** , sélectionnez **fichier dans le système de fichiers** , puis utilisez le bouton **Parcourir** pour sélectionner le VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Exiger une version spécifique de Visual Studio

Si votre extension nécessite une version spécifique de Visual Studio 2017, par exemple, elle dépend d’une fonctionnalité publiée dans 15,3, vous pouvez spécifier le numéro de build dans votre **le INSTALLATIONTARGET**VSIX. Par exemple, la version 15,3 a un numéro de Build « 15.0.26730.3 ». Vous pouvez voir [ici](../install/visual-studio-build-numbers-and-release-dates.md)le mappage des mises en production aux numéros de Build. Notez que l’utilisation du numéro de version « 15,3 » ne fonctionne pas correctement.

Si votre extension requiert 15,3 ou une version ultérieure, vous devez déclarer la **version de le installationtarget** en tant que [15.0.26730.3, 16,0) :

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller détecte les versions antérieures de Visual Studio et informe l’utilisateur qu’une mise à jour ultérieure est requise.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Préparer les extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)