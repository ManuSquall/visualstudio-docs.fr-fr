---
title: Utilitaire RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839962"
---
# <a name="regpkg-utility"></a>Utilitaire RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> La meilleure façon d’inscrire des packages dans Visual Studio consiste à utiliser des fichiers. pkgdef. Cela permet le déploiement d’extension sans avoir à accéder au registre système, ce qui est une condition requise pour le déploiement VSIX. Les fichiers pkgdef sont créés à l’aide de l' [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Pour plus d’informations sur le déploiement de package Visual Studio, consultez [expédition d’extensions Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 L’utilitaire RegPkg.exe inscrit un VSPackage auprès de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et le prépare au déploiement. Cet utilitaire est utilisé en arrière-plan pendant le développement VSPackage. Il s’exécute dans le cadre du processus de génération afin que vous puissiez générer et exécuter un VSPackage dans la ruche expérimentale.  
  
 RegPkg peut générer des scripts de Registre système dans plusieurs formats. Vous pouvez incorporer ces scripts dans des projets de déploiement tels que des projets. msi ou des fichiers d’ensemble d’outils XML Windows Installer.  
  
 RegPkg.exe se trouve généralement dans \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg suit la syntaxe suivante :  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root : racine  
 Effectue l’inscription sous le spécifié  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] racine.  
  
 /regfile : nom de fichier  
 Crée un fichier. reg au lieu de mettre à jour le registre.  Ne peut pas être utilisé avec/vrgfile ou/rgsfile ou/wixfile.  
  
 /rgsfile : nom de fichier  
 Crée un fichier. RGS au lieu de mettre à jour le registre.  Ne peut pas être utilisé avec/vrgfile ou/regfile ou/wixfile.  
  
 /vrgfile : nom de fichier  
 Crée un fichier. VRG au lieu de mettre à jour le registre.  Ne peut pas être utilisé avec/regfile ou/rgsfile ou/wixfile.  
  
 /rgm  
 Crée un fichier. RGM en plus du fichier RGS.  Doit être combiné avec/rgsfile.  
  
 /wixfile : nom de fichier  
 Crée un fichier compatible avec l’ensemble d’outils XML Windows Installer plutôt que de mettre à jour le registre.  Ne peut pas être utilisé avec/regfile ou/rgsfile ou/vrgfile.  
  
 /codebase  
 Force l’inscription avec code base plutôt que l’assembly.  
  
 /assembly  
 Force l’inscription avec l’assembly plutôt que le code base.  
  
 /Unregister  
 Annule l’inscription de ce package.  Ne peut pas être utilisé  
  
 avec/regfile,/vrgfile ou/rgsfile ou/wixfile.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’un produit](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Résolution des problèmes d’inscription du package RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
