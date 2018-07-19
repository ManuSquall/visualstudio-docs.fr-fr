---
title: IEnumDebugPropertyInfo2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cd2e15aa02004f6fe22f08894a7f3eec4c1ea22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124741"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Cette interface énumère [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter les informations pour une propriété particulière.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir cette interface représentant les enfants d’une propriété particulière. Appelez [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pour obtenir cette interface représentant les propriétés d’un frame de pile spécifique.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPropertyInfo2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Récupère un nombre spécifié de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignore un nombre spécifié de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtient le nombre de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 En règle générale, une propriété est une hiérarchie d’informations qui peuvent inclure un nom, valeur, adresse et le type, ainsi que d’autres informations appropriées pour le frame de pile ou objet de propriété associée. Consultez [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) pour plus d’informations.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)