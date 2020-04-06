---
title: IEnumDebugPortSuppliers2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de0bfc5b387df9b347e4a58d97601a5e1e70f1a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715934"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
Cette interface énumère les fournisseurs portuaires.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente cette interface pour représenter une liste de fournisseurs portuaires.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) pour obtenir une liste des fournisseurs portuaires.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugPortSuppliers2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Récupère un nombre précis de fournisseurs portuaires dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Il saute un nombre précis de fournisseurs portuaires dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Obtient le nombre de fournisseurs portuaires dans un enumérateur.|

## <a name="remarks"></a>Notes
 Un moteur de débogé n’a généralement pas besoin d’obtenir cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
