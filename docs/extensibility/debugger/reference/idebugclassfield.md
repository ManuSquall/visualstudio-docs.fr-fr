---
title: "IDebugClassField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField"
helpviewer_keywords: 
  - "Interface de IDebugClassField"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une classe comme type.  
  
## Syntaxe  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## Remarques à l'intention des implémenteurs  
 un fournisseur de symbole implémente cette interface sur le même objet qui implémente l'interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .  cette interface est une spécialisation qui représente un type de classe.  
  
## Remarques pour les appelants  
 Un nombre quelconque d'interfaces ont des méthodes qui peuvent retourner cette interface y compris [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), et [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).  En outre, vous pouvez utiliser [QueryInterface](/visual-cpp/atl/queryinterface) pour obtenir cette interface de l'interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si la méthode d' [GetKind](../Topic/IDebugField::GetKind.md) retourne la balise `FIELD_TYPE_CLASS`.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur des interfaces d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , cette interface implémente les éléments suivants :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumBaseClasses](../Topic/IDebugClassField::EnumBaseClasses.md)|crée un énumérateur pour les classes de base de cette classe.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|détermine si une interface spécifique est définie dans la classe.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|crée un énumérateur pour les classes imbriquées de cette classe.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Obtient la classe qui attache cette classe.|  
|[EnumInterfacesImplemented](../Topic/IDebugClassField::EnumInterfacesImplemented.md)|crée un énumérateur pour les interfaces implémentées par cette classe.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|crée un énumérateur pour les constructeurs de cette classe.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|obtient le nom de l'indexeur par défaut.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|crée un énumérateur pour les énumérateurs imbriqués de cette classe.|  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)