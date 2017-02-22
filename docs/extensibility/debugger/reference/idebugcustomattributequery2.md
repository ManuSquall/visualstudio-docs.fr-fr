---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "Interface de IDebugCustomAttributeQuery"
  - "Interface de IDebugCustomAttributeQuery2"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détermine l'existence d'un attribut personnalisé de ce champ et, s'il existe, retourne les informations d'attribut.  
  
## Syntaxe  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de symbole implémente cette interface sur le même objet qui implémente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pour prendre en charge les attributs personnalisés.  
  
## Remarques pour les appelants  
 utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface de l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d'interface **d'IDebugCustomAttributeQuery** .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|détermine si un attribut personnalisé existe de nom.|  
|[GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md)|obtient les informations d'attribut pour l'attribut personnalisé donné.|  
  
 En plus de les méthodes **d'IDebugCustomAttributeQuery** , `IDebugCustomAttributeQuery2` implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtient un énumérateur pour tous les attributs personnalisés attachés à ce champ.|  
  
## Notes  
 la méthode d' [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) peut retourner un énumérateur pour tous les attributs personnalisés définis pour ce champ.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)