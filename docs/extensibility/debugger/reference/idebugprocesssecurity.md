---
title: IDebugProcessSecurity (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723187"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`est mis en œuvre par un fournisseur de port pour avertir l’utilisateur que l’attachement au processus est dangereux.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProcessSecurity`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetUserName (en)](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtient le nom d’utilisateur du fournisseur de port.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Avertit un utilisateur que l’attachement au processus de débogage est dangereux.|

## <a name="remarks"></a>Notes
 Implémentez cette interface pour afficher un avertissement et permettre à l’utilisateur d’annuler si le processus auquel vous attachez peut être considéré comme dangereux.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Ports](../../../extensibility/debugger/ports.md)
- [Fournisseurs de ports](../../../extensibility/debugger/port-suppliers.md)
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
