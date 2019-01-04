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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3f9eecfaeffd19ece7e0ca2fe14e3f95556503d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904875"
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
  
 /root:root  
 Effectue des processus d’inscription spécifié  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine.  
  
 /regfile:filename  
 Crée un fichier .reg, plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /vrgfile ou /rgsfile ou /wixfile.  
  
 /rgsfile:filename  
 Crée un fichier .rgs plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /vrgfile ou /regfile ou /wixfile.  
  
 /vrgfile:filename  
 Crée un fichier .vrg plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /regfile ou /rgsfile ou /wixfile.  
  
 /RGM  
 Crée un fichier .rgm en plus du fichier rgs.  Doit être combinée avec /rgsfile.  
  
 /wixfile:filename  
 Crée un fichier compatible avec Windows Installer XML Toolset plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /regfile ou /rgsfile ou /vrgfile.  
  
 /codebase  
 Inscription de force avec la base de code plutôt que d’Assembly.  
  
 assembly  
 Inscription de force avec l’Assembly plutôt que de base de code.  
  
 / Annuler l’inscription  
 Annule l’inscription de ce package.  Ne peut pas être utilisé.  
  
 avec /regfile /vrgfile ou /rgsfile ou /wixfile.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 [Résolution des problèmes d’inscription du package RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)