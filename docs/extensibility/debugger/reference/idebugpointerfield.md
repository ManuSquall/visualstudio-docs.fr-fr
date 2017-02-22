---
title: "IDebugPointerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField"
helpviewer_keywords: 
  - "Interface de IDebugPointerField"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un type pointeur.  
  
## Syntaxe  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## Remarques à l'intention des implémenteurs  
 le fournisseur de symbole implémente cette interface pour représenter un pointeur.  
  
## Remarques pour les appelants  
 Utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface de l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../Topic/IDebugField::GetKind.md) retourne `FIELD_TYPE_POINTER`.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur des interfaces d' `IDebugField` et d' `IDebugContainerField` , cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Retourne [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant la cible du pointeur.|  
  
## Notes  
 En C\/C\+\+, un pointeur peut être un conteneur s'il est utilisé avec la notation de tableau.  Par exemple, si `char *pString`, `pString` possède un type de pointeur vers `char`.  `pString[3]` a le type d'un conteneur qui est un pointeur vers `char` qui référence le quatrième élément de ce conteneur.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)