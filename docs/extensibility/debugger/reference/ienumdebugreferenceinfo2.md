---
title: "IEnumDebugReferenceInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2"
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les structures de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
## Syntaxe  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface dans le cadre de son prise en charge des références aux objets en mémoire.  Cette interface doit être implémentée uniquement si les références sont prises en charge.  
  
## Remarques pour les appelants  
 Visual Studio appelle [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugReferenceInfo2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Récupère un nombre spécifié de structures de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignore un nombre spécifié de structures de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans la séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|obtient le nombre de structures de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans un énumérateur.|  
  
## Notes  
 Une référence est essentiellement un type et une adresse, alors qu'une propriété est un nom, un type, et une adresse.  Une référence est maintenu tant que l'objet référencé existe dans la mémoire.  Pour plus d'informations, consultez [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)