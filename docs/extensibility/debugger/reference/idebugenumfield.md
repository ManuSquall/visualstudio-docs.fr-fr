---
title: "IDebugEnumField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField"
helpviewer_keywords: 
  - "Interface de IDebugEnumField"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un type énumération.  
  
## Syntaxe  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## Remarques à l'intention des implémenteurs  
 un fournisseur de symbole implémente cette interface pour représenter une énumération.  
  
## Remarques pour les appelants  
 Utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface de l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../Topic/IDebugField::GetKind.md) retourne `FIELD_TYPE_ENUM`.  
  
## méthodes en commande de VTable  
 En plus de les méthodes sur des interfaces d' `IDebugField` et d' `IDebugContainerField` , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Retourne [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant le nom de ce type énumération.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Retourne le nom de la constante d'énumération associée à la valeur donnée.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Retourne la valeur associée au nom de la constante donné d'énumération|  
|[GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)|Retourne la valeur associée au nom de la constante donné d'énumération mais ignorante le cas.|  
  
## Notes  
 Il s'agit du symbole sous\-jacent qui est lié en fait à un emplacement à [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)