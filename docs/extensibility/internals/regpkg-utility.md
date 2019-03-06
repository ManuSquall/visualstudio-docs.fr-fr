---
title: Utilitaire RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b9b07bc801e687da9ce93968dbac59966328484
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619236"
---
# <a name="regpkg-utility"></a>Utilitaire RegPkg
> [!NOTE]
>  La meilleure façon d’enregistrer des packages dans Visual Studio est à l’aide de fichiers .pkgdef. Cela permet le déploiement de l’extension sans avoir à accéder au Registre système, qui est nécessaire pour le déploiement VSIX. Fichiers pkgdef sont créés à l’aide de la [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Pour plus d’informations sur le déploiement de package Visual Studio, consultez [de livraison des Extensions Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 L’utilitaire RegPkg.exe inscrit un VSPackage avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le prépare pour le déploiement. Cet utilitaire est utilisé en arrière-plan pendant le développement de VSPackage. Il s’exécute dans le cadre du processus de génération afin que vous pouvez générer et exécuter un VSPackage dans la ruche expérimentale.

 RegPkg peut générer des scripts de Registre système dans plusieurs formats. Vous pouvez incorporer ces scripts dans les projets de déploiement telles que les projets .msi ou des fichiers de Windows Installer XML Toolset.

 RegPkg.exe est généralement situé à \< *chemin d’installation de Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg suit cette syntaxe :

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root effectue processus d’inscription spécifié

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine.

 /regfile:filename crée un fichier .reg, plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /vrgfile ou /rgsfile ou /wixfile.

 /rgsfile:filename crée un fichier .rgs plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /vrgfile ou /regfile ou /wixfile.

 /vrgfile:filename crée un fichier .vrg plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /regfile ou /rgsfile ou /wixfile.

 /RGM crée un fichier .rgm en plus du fichier rgs.  Doit être combinée avec /rgsfile.

 /wixfile:filename crée un fichier compatible avec Windows Installer XML Toolset plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /regfile ou /rgsfile ou /vrgfile.

 / base de code d’inscription de force avec la base de code plutôt que d’Assembly.

 inscription de force /assembly avec l’Assembly plutôt que de base de code.

 /unregister unregister ce package.  Ne peut pas être utilisé.

 avec /regfile /vrgfile ou /rgsfile ou /wixfile.

## <a name="see-also"></a>Voir aussi
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Résolution des problèmes d’inscription du package RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)