---
title: Service public RegPkg (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705634"
---
# <a name="regpkg-utility"></a>Utilitaire RegPkg
> [!NOTE]
> La meilleure façon d’enregistrer des paquets dans Visual Studio est d’utiliser des fichiers .pkgdef. Cela permet le déploiement d’extension sans avoir à accéder au registre du système, ce qui est une exigence pour le déploiement de VSIX. Les fichiers Pkgdef sont créés en utilisant le [Service utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Pour plus d’informations sur le déploiement du forfait Visual Studio, voir [Extensions De studio visuel d’expédition](../../extensibility/shipping-visual-studio-extensions.md).

 L’utilitaire RegPkg.exe enregistre un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage avec et le prépare pour le déploiement. Cet utilitaire est utilisé dans les coulisses pendant le développement VSPackage. Il s’exécute dans le cadre du processus de construction afin que vous puissiez construire et exécuter un VSPackage dans la ruche expérimentale.

 RegPkg peut générer des scripts de registre système en plusieurs formats. Vous pouvez intégrer ces scripts dans des projets de déploiement tels que des projets .msi ou des fichiers Windows Installer XML Toolset.

 RegPkg.exe est généralement \<situé à *Visual Studio SDK chemin d’installation*>-VisualStudioIntegration-Tools -Bin-RegPkg.exe. RegPkg suit cette syntaxe :

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Effectue l’enregistrement sous le spécifié

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine.

 /regfile:FileName Crée un fichier .reg plutôt que de mettre à jour le registre.  Impossible d’utiliser avec /vrgfile ou /rgsfile ou /wixfile.

 /rgsfile:FileName Crée un fichier .rgs plutôt que de mettre à jour le registre.  Impossible d’utiliser avec /vrgfile ou /regfile ou /wixfile.

 /vrgfile:FileName Crée un fichier .vrg plutôt que de mettre à jour le registre.  Impossible d’utiliser avec /regfile ou /rgsfile ou /wixfile.

 /rgm Crée un fichier .rgm en plus du fichier rgs.  Doit être combiné avec /rgsfile.

 /wixfile:FileName crée un fichier compatible Windows Install XML Toolset plutôt que de mettre à jour le registre.  Impossible d’utiliser avec /regfile ou /rgsfile ou /vrgfile.

 /codebase Forces enregistrement avec CodeBase plutôt que l’Assemblage.

 /l’enregistrement des forces d’assemblage auprès de l’Assemblée plutôt que de CodeBase.

 /unregister Unregisters ce paquet.  Impossible d’utiliser

 avec /regfile ou /vrgfile ou /rgsfile ou /wixfile.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Résolution des problèmes d’inscription du package RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
