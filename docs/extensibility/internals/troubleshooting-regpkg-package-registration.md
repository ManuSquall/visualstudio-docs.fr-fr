---
title: Résolution des problèmes d’inscription du package RegPkg | Microsoft Docs
description: Utilisez ces informations pour résoudre les problèmes liés à l’inscription de packages RegPkg dans Visual Studio. Utilisez la version de RegPkg appropriée pour votre package.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48e3699b095ed7b9d0e72cf7b09ad02e26ac5a51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090757"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Résolution des problèmes d’inscription du package RegPkg
> [!NOTE]
> La meilleure façon d’inscrire des packages dans Visual Studio consiste à utiliser des fichiers. pkgdef. Cela permet le déploiement d’extension sans avoir à accéder au registre système. Les fichiers pkgdef sont créés à l’aide de l' [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Pour inscrire un package à l’aide de RegPkg dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , vous devez utiliser la version de regpkg appropriée pour votre package.

## <a name="regpkg-versions-related-to-package-versions"></a>Versions de RegPkg relatives aux versions de package
 Il existe deux versions de RegPkg. Une version est incluse dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Utilisez cette version pour inscrire des packages qui ont été générés à l’aide de l’un des assemblys suivants :

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Il ne peut pas inscrire des packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll antérieur.

   La version antérieure de RegPkg peut inscrire des packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll. Toutefois, il ne peut pas inscrire les packages générés à l’aide des versions ultérieures de cet assembly.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
