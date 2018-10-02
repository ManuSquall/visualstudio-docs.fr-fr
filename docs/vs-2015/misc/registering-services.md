---
title: Inscription de Services | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504006"
---
# <a name="registering-services"></a>Inscription de services
Pour prendre en charge le chargement à la demande, un fournisseur de services doit inscrire ses services globaux auprès [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Pendant le développement, fournisseurs de services gérés inscrivent les services et les remplacements de service en ajoutant des attributs au code source pour les packages et puis en générant les packages le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Cela exécute l’utilitaire RegPkg.exe sur l’assembly résultant, ce qui inscrit le package et le prépare pour le déploiement. Pour plus d’informations, consultez [Comment : inscrire un Service](../misc/how-to-register-a-service.md).  
  
 Fournisseurs de services non managé doivent inscrire les services qu’ils fournissent avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dans les services de section ou le service se substitue à la section du Registre système. Le fragment de fichier .reg suivant montre comment le service, SVsTextManager, peut être inscrit :  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 Dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], par exemple 7.1 ou 8.0, la clé {F5E7E71D-1401-11d1-883B-0000F87579D2} est l’identificateur de service (SID) du service, SVsTextManager et la {valeur par défaut F5E7E720-1401-11D1-883B-0000F87579D2} est le GUID du package le VSPackage, qui fournit le service de gestionnaire de texte.  
  
## <a name="remote-services-and-background-threads"></a>Services distants et threads d’arrière-plan  
 Les services que vous fournissez ne sont pas automatiquement disponibles à distance ou pour les threads d’arrière-plan. Pour les rendre disponibles, vous devez générer et inscrire une bibliothèque de types.  
  
 À partir du code non managé qui utilise Visual Studio Library (VSL), vous pouvez inscrire votre bibliothèque de types en procédant comme suit :  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 À partir du code managé, vous pouvez ajouter une étape post-build en procédant comme suit :  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)