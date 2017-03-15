---
title: "Inscription de services | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, inscrire"
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Inscription de services
Pour prendre en charge le chargement à la demande, un fournisseur de services doit inscrire ses services globaux auprès de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Pendant le développement, les fournisseurs de services gérés inscrivent les services et les remplacements de services en ajoutant des attributs au code source des packages, et puis en générant les packages dans l’IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Cela exécute l’utilitaire RegPkg.exe sur l’assembly résultant, ce qui inscrit le package et le prépare pour le déploiement. Pour plus d'informations, consultez [Procédure : inscription d’un service](../misc/how-to-register-a-service.md).  
  
 Les fournisseurs de services non géré doivent inscrire les services qu’ils fournissent auprès de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la section de services ou la section de remplacements de services du Registre système. Le fragment de fichier .reg suivant montre comment le service, SVsTextManager, peut être inscrit :  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
```  
  
 Dans l’exemple ci\-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 7.1 ou 8.0, la clé {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} est l’identificateur de service \(SID\) du service, SVsTextManager, et la valeur par défaut {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} est le GUID du package Visual Studio de gestionnaire de texte, qui fournit le service.  
  
## Services distants et threads d’arrière\-plan  
 Les services que vous fournissez ne sont pas automatiquement disponibles à distance ou pour les threads d’arrière\-plan. Pour les rendre disponibles, vous devez générer et inscrire une bibliothèque de types.  
  
 À partir du code non managé qui utilise Visual Studio Library \(VSL\), vous pouvez inscrire votre bibliothèque de types en procédant comme suit :  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE #include <VSLPackageDllEntryPoints.cpp>  
```  
  
 À partir du code managé, vous pouvez ajouter une étape post\-build en procédant comme suit :  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## Voir aussi  
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)