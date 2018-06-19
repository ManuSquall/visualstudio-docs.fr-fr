---
title: IDebugCustomAttribute | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0d7497f5fcda3b871c5a1ad57cf04767617bdab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107762"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Cette interface représente un attribut personnalisé, et il peut fournir le nom, le parent et le type de classe de l’attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de symbole implémente cette interface pour prendre en charge les attributs personnalisés associés à un symbole. Il est généralement implémentée sur son propre objet.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retourne cette interface. Un appel à la [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) méthode retourne la [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugCustomAttribute`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtient le champ auquel l’attribut actuel est attaché.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtient le type de classe d’attribut personnalisé.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtient le nom de l’attribut personnalisé.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtient les informations d’attribut comme un objet blob d’octets.|  
  
## <a name="remarks"></a>Notes  
 Un attribut personnalisé est une structure de C# qui fournit des métadonnées personnalisées associées à une classe particulière ou une méthode.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)