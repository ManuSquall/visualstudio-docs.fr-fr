---
title: "IDebugMethodField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField"
helpviewer_keywords: 
  - "Interface de IDebugMethodField"
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMethodField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface décrit une méthode.  
  
## Syntaxe  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## Remarques à l'intention des implémenteurs  
 un fournisseur de symbole implémente cette interface sur le même objet qui implémente l'interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .  cette interface est une spécialisation qui présente une méthode.  
  
## Remarques pour les appelants  
 Utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface de l'interface d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si [GetKind](../Topic/IDebugField::GetKind.md) retourne `FIELD_TYPE_METHOD`.  En outre, les méthodes, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), et [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), tout retournent l'interface d' `IDebugMethodField` .  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur des interfaces d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) et d' [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|crée un énumérateur pour les paramètres de la méthode.|  
|[Get :](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtient le pointeur « this » de l'objet contenant la méthode.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|crée un énumérateur pour toutes les variables locales de la méthode.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Crée un énumérateur pour les variables locales sélectionnées de la méthode.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|détermine si un attribut personnalisé spécifique a été défini.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Crée un énumérateur pour les variables locales statiques de la méthode.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|obtient le conteneur global de la méthode.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.|  
  
## Notes  
 Une méthode peut contenir des paramètres ainsi que des variables locales.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)