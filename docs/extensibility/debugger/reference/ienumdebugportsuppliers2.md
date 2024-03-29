---
description: Cette interface énumère les fournisseurs de port.
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82841ab033091d2fd3c88c64dfb81d1f5d2e2468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073441"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Cette interface énumère les fournisseurs de port.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface pour représenter une liste de fournisseurs de ports.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) pour obtenir la liste des fournisseurs de port.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugPortSuppliers2` .

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Récupère un nombre spécifié de fournisseurs de ports dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Ignore un nombre spécifié de fournisseurs de ports dans une séquence d’énumération.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Obtient le nombre de fournisseurs de port dans un énumérateur.|

## <a name="remarks"></a>Notes
 Un moteur de débogage n’a généralement pas besoin d’obtenir cette interface.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
