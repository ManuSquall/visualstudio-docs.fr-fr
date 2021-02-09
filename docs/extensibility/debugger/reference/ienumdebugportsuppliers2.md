---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: edff2cad101a6a6f0f19a4b384b8f2398b98b2e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883738"
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
|[Répliqué](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Obtient le nombre de fournisseurs de port dans un énumérateur.|

## <a name="remarks"></a>Remarques
 Un moteur de débogage n’a généralement pas besoin d’obtenir cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
