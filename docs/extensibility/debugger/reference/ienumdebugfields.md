---
title: "IEnumDebugFields | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "Interface de IEnumDebugFields"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une collection d'objets implémentant l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Syntaxe  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 cette interface est implémentée par le fournisseur de symbole pour fournir des ensembles d'objets qui implémentent l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  Notez que ce n'est pas une énumération standard COM en raison de la présence de la méthode d' [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .  
  
## Remarques pour les appelants  
 cette interface est retournée par [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md) et [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## méthodes en commande de Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|extrait l'ensemble suivant d'objets d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de l'énumération.|  
|[Ignorer](../Topic/IEnumDebugFields::Skip.md)|Ignore un nombre spécifié d'entrées.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|réinitialise l'énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|extrait une copie de l'énumération actuelle.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Récupère le nombre d'entrées de l'énumération.|  
  
## Notes  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)