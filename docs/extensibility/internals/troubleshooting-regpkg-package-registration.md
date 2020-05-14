---
title: Enregistrement du forfait RegPkg de dépannage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704327"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Résolution des problèmes d’inscription du package RegPkg
> [!NOTE]
> La meilleure façon d’enregistrer des paquets dans Visual Studio est d’utiliser des fichiers .pkgdef. Cela permet le déploiement d’extension sans avoir à accéder au registre du système. Les fichiers Pkgdef sont créés en utilisant le [Service utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Pour enregistrer un paquet en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilisant RegPkg, vous devez utiliser la version de RegPkg qui est approprié pour votre paquet.

## <a name="regpkg-versions-related-to-package-versions"></a>Versions RegPkg liées aux versions de paquets
 Il existe deux versions de RegPkg. Une version est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]incluse dans . Utilisez cette version pour enregistrer les paquets qui ont été construits en utilisant l’un des assemblages suivants :

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Il ne peut pas enregistrer les paquets qui ont été construits en utilisant l’assemblage Microsoft.VisualStudio.Shell.dll plus tôt.

   La version antérieure de RegPkg peut enregistrer les paquets qui ont été construits en utilisant l’assemblage Microsoft.VisualStudio.Shell.dll. Toutefois, il ne peut pas enregistrer les paquets construits en utilisant des versions ultérieures de cet assemblage.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
