---
title: Utilitaire RegPkg | Microsoft Docs
description: Découvrez comment l’utilitaire RegPkg.exe inscrit un VSPackage auprès de Visual Studio et le prépare au déploiement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b605d251b2e516a468401805fc0e125801129c16
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903357"
---
# <a name="regpkg-utility"></a>Utilitaire RegPkg
> [!NOTE]
> La meilleure façon d’inscrire des packages dans Visual Studio consiste à utiliser des fichiers. pkgdef. Cela permet le déploiement d’extension sans avoir à accéder au registre système, ce qui est une condition requise pour le déploiement VSIX. Les fichiers pkgdef sont créés à l’aide de l' [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Pour plus d’informations sur le déploiement de package Visual Studio, consultez [expédition d’extensions Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 L’utilitaire RegPkg.exe inscrit un VSPackage auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le prépare au déploiement. Cet utilitaire est utilisé en arrière-plan pendant le développement VSPackage. Il s’exécute dans le cadre du processus de génération afin que vous puissiez générer et exécuter un VSPackage dans la ruche expérimentale.

 RegPkg peut générer des scripts de Registre système dans plusieurs formats. Vous pouvez incorporer ces scripts dans des projets de déploiement tels que des projets de .msi ou des fichiers d’ensemble d’outils XML Windows Installer.

 RegPkg.exe se trouve généralement dans \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg suit la syntaxe suivante :

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root : la racine effectue l’inscription sous la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine spécifiée.

 /regfile : FileName crée un fichier. reg au lieu de mettre à jour le registre.  Ne peut pas être utilisé avec/vrgfile ou/rgsfile ou/wixfile.

 /rgsfile : FileName crée un fichier. RGS au lieu de mettre à jour le registre.  Ne peut pas être utilisé avec/vrgfile ou/regfile ou/wixfile.

 /vrgfile : FileName crée un fichier. VRG au lieu de mettre à jour le registre.  Ne peut pas être utilisé avec/regfile ou/rgsfile ou/wixfile.

 /RGM crée un fichier. RGM en plus du fichier RGS.  Doit être combiné avec/rgsfile.

 /wixfile : FileName crée un fichier compatible avec l’ensemble d’outils XML Windows Installer plutôt que de mettre à jour le registre.  Ne peut pas être utilisé avec/regfile ou/rgsfile ou/vrgfile.

 /CodeBase force l’inscription avec le code base plutôt que l’assembly.

 /assembly force l’inscription avec l’assembly plutôt que le code base.

 /Unregister annule l’inscription de ce package.  Ne peut pas être utilisé

 avec/regfile,/vrgfile ou/rgsfile ou/wixfile.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Résolution des problèmes d’inscription du package RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
