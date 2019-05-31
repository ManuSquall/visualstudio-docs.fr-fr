---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbf6e2f5c644f340ca2c1ebba1d53fc026b0534b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322697"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Cette interface énumère [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter des informations pour une propriété particulière.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir cette interface représentant les enfants d’une propriété particulière. Appelez [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pour obtenir cette interface représentant les propriétés d’un frame de pile spécifique.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugPropertyInfo2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Récupère un nombre spécifié de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignore un nombre spécifié de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtient le nombre de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structures dans un énumérateur.|

## <a name="remarks"></a>Notes
 En règle générale, une propriété est une hiérarchie d’informations qui peuvent inclure un nom, valeur, adresse et le type, ainsi que toute autre information appropriée vers le frame de pile ou objet de propriété associée. Consultez [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) pour plus d’informations.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)