---
title: Résolution des problèmes d’inscription du Package RegPkg | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5b2ebc470d12586957d77bbe7b076c053567742
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495508"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Résolution des problèmes d’inscription du package RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [dépannage de l’inscription du Package RegPkg](https://docs.microsoft.com/visualstudio/extensibility/internals/troubleshooting-regpkg-package-registration).  
  
> [!NOTE]
>  La meilleure façon d’enregistrer des packages dans Visual Studio est à l’aide de fichiers .pkgdef. Cela permet le déploiement de l’extension sans avoir à accéder au Registre système. Fichiers pkgdef sont créés à l’aide de la [utilitaire CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Inscription d’un package à l’aide de RegPkg dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vous devez utiliser la version de RegPkg qui convient à votre package.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Versions RegPkg relatives aux Versions de Package  
 Il existe deux versions de RegPkg. Une version est incluse dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Utilisez cette version pour inscrire les packages qui ont été générés à l’aide d’un des assemblys suivants :  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 Elle ne peut pas inscrire les packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll antérieures.  
  
 La version antérieure de RegPkg peut inscrire des packages qui ont été générés à l’aide de l’assembly Microsoft.VisualStudio.Shell.dll. Toutefois, elle ne peut pas inscrire les packages générés à l’aide des versions ultérieures de cet assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’un produit](../../misc/releasing-a-visual-studio-integration-product.md)

