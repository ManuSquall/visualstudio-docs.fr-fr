---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9200c5366fb428371b633cfb0b97f72d8da8b566
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693216"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Cette interface énumère les fournisseurs de port.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Visual Studio implémente cette interface pour représenter une liste de fournisseurs de port.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) pour obtenir une liste de fournisseurs de port.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugPortSuppliers2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Récupère un nombre spécifié de fournisseurs de port dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignore un nombre spécifié de fournisseurs de port dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Obtient le nombre de fournisseurs de port dans l’énumérateur.|

## <a name="remarks"></a>Notes
 Un moteur de débogage n’a généralement pas besoin d’obtenir cette interface.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)