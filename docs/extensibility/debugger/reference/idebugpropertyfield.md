---
title: "IDebugPropertyField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "Interface de IDebugPropertyField"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface fournit les fonctions qui permettent d'obtenir et de définir une propriété.  
  
## Syntaxe  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## Remarques à l'intention des implémenteurs  
 un fournisseur de symbole implémente cette interface sur le même objet qui implémente [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md).  cette interface est une spécialisation qui prend en charge le concept des propriétés sur une classe.  
  
## Remarques pour les appelants  
 Utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface de l'interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si la méthode d' [GetKind](../Topic/IDebugField::GetKind.md) retourne `FIELD_KIND_PROP`.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur des interfaces d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Obtient la méthode qui reçoit la propriété.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|obtient la méthode qui définit la propriété.|  
  
## Notes  
 Une propriété est un concept de code managé et représente une méthode qui est traitée comme une variable.  Les propriétés n'existent pas dans le code C\+\+ non managé.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)