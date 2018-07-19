---
title: Utilitaire RegPkg | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5d677aaf155e533c27a775f3995b53dd59b65385
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130946"
---
# <a name="regpkg-utility"></a>Utilitaire RegPkg
> [!NOTE]
>  La meilleure méthode pour enregistrer des packages dans Visual Studio est à l’aide de fichiers de .pkgdef. Ainsi, pour le déploiement d’une extension sans avoir à accéder au Registre du système, qui est requis pour le déploiement VSIX. Fichiers de pkgdef sont créés à l’aide de la [CreatePkgDef utilitaire](../../extensibility/internals/createpkgdef-utility.md). Pour plus d’informations sur le déploiement de package Visual Studio, consultez [de livraison des Extensions Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 L’utilitaire RegPkg.exe enregistre un VSPackage avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et le prépare pour le déploiement. Cet utilitaire est utilisé en arrière-plan pendant le développement du VSPackage. Il s’exécute dans le cadre du processus de génération afin que vous pouvez générer et exécuter un VSPackage dans la ruche expérimentale.  
  
 RegPkg peut générer des scripts de Registre du système dans plusieurs formats. Vous pouvez incorporer ces scripts dans les projets de déploiement, tels que les projets .msi ou ensemble d’outils XML de Windows Installer.  
  
 RegPkg.exe se trouve généralement à \< *chemin d’installation de Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg suit cette syntaxe :  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Effectue l’enregistrement sous le  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] racine.  
  
 /regfile:filename  
 Crée un fichier .reg plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /vrgfile ou /rgsfile ou /wixfile.  
  
 /rgsfile:filename  
 Crée un fichier .rgs plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /vrgfile ou /regfile ou /wixfile.  
  
 /vrgfile:filename  
 Crée un fichier .vrg, plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /regfile ou /rgsfile ou /wixfile.  
  
 /RGM  
 Crée un fichier .rgm en plus du fichier rgs.  Doit être combiné avec /rgsfile.  
  
 /wixfile:filename  
 Crée un fichier compatible ensemble d’outils XML de Windows Installer, plutôt que de la mise à jour le Registre.  Ne peut pas être utilisé avec /regfile ou /rgsfile ou /vrgfile.  
  
 /codebase  
 Force l’inscription auprès CodeBase plutôt que d’Assembly.  
  
 / assembly  
 Inscription de force avec Assembly plutôt que de base de code.  
  
 /unregister  
 Annule l’inscription de ce package.  Ne peut pas être utilisé.  
  
 avec /regfile ou /vrgfile ou /rgsfile ou /wixfile.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 [Résolution des problèmes d’inscription du package RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)