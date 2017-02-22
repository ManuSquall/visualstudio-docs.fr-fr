---
title: "IEnumDebugCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes"
helpviewer_keywords: 
  - "Interface de IEnumDebugCustomAttributes"
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Énumère les attributs personnalisés.  
  
## Syntaxe  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de symbole implémente cette interface pour prendre en charge les attributs personnalisés \(via l'interface d' [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) \).  
  
## Remarques pour les appelants  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retourne cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugCustomAttributes`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Extrait un nombre spécifié d'attributs personnalisés dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Ignore un nombre spécifié d'attributs personnalisés dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../Topic/IEnumDebugCustomAttributes::Clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|obtient le nombre d'attributs personnalisés dans un énumérateur.|  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)