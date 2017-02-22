---
title: "IEnumCodePaths2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2"
helpviewer_keywords: 
  - "Interface de IEnumCodePaths2"
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une liste de chemins de code.  
  
## Syntaxe  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour représenter une liste de chemins de code.  
  
## Remarques pour les appelants  
 appel [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumCodePaths2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Récupère un nombre spécifié de chemins de code dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignore un nombre spécifié de chemins de code dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../Topic/IEnumCodePaths2::GetCount.md)|obtient le nombre de chemins de code dans un énumérateur.|  
  
## Notes  
 Un chemin de code représente un point de branche ou un appel de fonction dans un programme.  Une liste de chemins de code représente le chemin d'accès dans lequel l'exécution de code l'a pris.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)