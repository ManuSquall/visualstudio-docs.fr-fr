---
title: IEnumDebugPropertyInfo2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715355"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Cette interface énumère [les structures DEBUG_PROPERTY_INFO.](../../../extensibility/debugger/reference/debug-property-info.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter les informations pour une propriété particulière.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) pour obtenir cette interface représentant les enfants d’une propriété particulière. Appelez [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) pour obtenir cette interface représentant les propriétés d’un cadre de pile particulier.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugPropertyInfo2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Récupère un nombre précis de structures [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Passe un nombre précis de structures [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtient le nombre de structures [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) dans un enumérateur.|

## <a name="remarks"></a>Notes
 En général, une propriété est une hiérarchie d’informations qui peut inclure un nom, une valeur, une adresse et un type, ainsi que toute autre information appropriée à l’objet de propriété associé ou cadre de pile. Voir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) pour plus de détails.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
