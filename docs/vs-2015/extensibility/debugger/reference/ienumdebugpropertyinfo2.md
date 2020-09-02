---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee305083957f6d2f2ada09aec1747497fcf6db68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147829"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface énumère les structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur DE débogage (DE) implémente cette interface pour représenter des informations pour une propriété particulière.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Appelez [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir cette interface représentant les enfants d’une propriété particulière. Appelez [EnumProperties,](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pour obtenir cette interface représentant les propriétés d’un frame de pile particulier.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPropertyInfo2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Récupère un nombre spécifié de structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignore un nombre spécifié de structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Réinitialise une séquence d'énumération.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtient le nombre de structures de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 En général, une propriété est une hiérarchie d’informations qui peut inclure un nom, une valeur, une adresse et un type, ainsi que toute autre information appropriée à l’objet de propriété ou au frame de pile associé. Pour plus d’informations, consultez [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
