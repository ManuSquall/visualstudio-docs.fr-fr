---
title: Résolution des problèmes d’inscription du Package RegPkg | Microsoft Docs
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
ms.openlocfilehash: 5424ca9a1a51088a020d04faa55754ad487d5723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910535"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Résolution des problèmes d’inscription du package RegPkg
> [!NOTE]
>  La meilleure façon d’enregistrer des packages dans Visual Studio est à l’aide de fichiers .pkgdef. Cela permet le déploiement de l’extension sans avoir à accéder au Registre système. Fichiers pkgdef sont créés à l’aide de la [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Inscription d’un package à l’aide de RegPkg dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous devez utiliser la version de RegPkg qui convient à votre package.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versions RegPkg relatives aux Versions de Package  
 Il existe deux versions de RegPkg. Une version est incluse dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Utilisez cette version pour inscrire les packages qui ont été générés à l’aide d’un des assemblys suivants :  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Elle ne peut pas inscrire les packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll antérieures.  
  
   La version antérieure de RegPkg peut inscrire des packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll. Toutefois, elle ne peut pas inscrire les packages générés à l’aide des versions ultérieures de cet assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../../extensibility/internals/vspackages.md)