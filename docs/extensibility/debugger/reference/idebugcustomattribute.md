---
title: "IDebugCustomAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute"
helpviewer_keywords: 
  - "Interface de IDebugCustomAttribute"
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un attribut personnalisé, et il peut fournir le nom, le parent, et le type de classe de l'attribut.  
  
## Syntaxe  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de symbole implémente cette interface pour prendre en charge les attributs personnalisés associés à un symbole.  Il est généralement implémenté dans son propre objet.  
  
## Remarques pour les appelants  
 Un appel à [Suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retourne cette interface.  Un appel à la méthode d' [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retourne l'interface d' [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugCustomAttribute`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetParentField](../Topic/IDebugCustomAttribute::GetParentField.md)|Obtient le champ auquel l'attribut actuel est attaché.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtient le type de classe personnalisée d'attributs.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|obtient le nom de l'attribut personnalisé.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtient les informations d'attribut comme un blob des octets.|  
  
## Notes  
 Un attribut personnalisé est une structure pour c\# qui fournit des métadonnées personnalisées associées à une classe ou une méthode particulière.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)