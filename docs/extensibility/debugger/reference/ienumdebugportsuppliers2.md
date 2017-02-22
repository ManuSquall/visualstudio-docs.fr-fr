---
title: "IEnumDebugPortSuppliers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2"
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les fournisseurs de port.  
  
## Syntaxe  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente cette interface pour représenter une liste des fournisseurs de port.  
  
## Remarques pour les appelants  
 Appelez [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) pour obtenir une liste des fournisseurs de port.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugPortSuppliers2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../Topic/IEnumDebugPortSuppliers2::Next.md)|Récupère un nombre spécifié de fournisseurs de port dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignore un nombre spécifié de fournisseurs de port dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../Topic/IEnumDebugPortSuppliers2::Clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|obtient le nombre de fournisseurs de port dans un énumérateur.|  
  
## Notes  
 Un moteur de débogage n'est en général pas besoin d'obtenir cette interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)