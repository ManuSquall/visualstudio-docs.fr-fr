---
title: Résolution des problèmes d’inscription du Package de RegPkg | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-regpkg-package-registration"></a>Résolution des problèmes d’inscription du Package de RegPkg
> [!NOTE]
>  La meilleure méthode pour enregistrer des packages dans Visual Studio est à l’aide de fichiers de .pkgdef. Ainsi, pour le déploiement d’une extension sans avoir à accéder au Registre système. Fichiers de pkgdef sont créés à l’aide de la [CreatePkgDef utilitaire](../../extensibility/internals/createpkgdef-utility.md).  
  
 Pour enregistrer un package à l’aide de RegPkg dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez utiliser la version de RegPkg qui est appropriée pour votre package.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versions RegPkg relatives aux Versions de Package  
 Il existe deux versions de RegPkg. Une version est incluse dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Cette version permet d’enregistrer des packages qui ont été générés à l’aide d’un des assemblys suivants :  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Il ne peut pas enregistrer les packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll antérieur.  
  
 La version antérieure de RegPkg peut enregistrer des packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll. Toutefois, il ne peut pas inscrire les packages créés à l’aide des versions ultérieures de cet assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../../extensibility/internals/vspackages.md)