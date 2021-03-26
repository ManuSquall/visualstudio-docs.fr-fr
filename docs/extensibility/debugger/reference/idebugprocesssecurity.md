---
description: IDebugProcessSecurity est implémenté par un fournisseur de port pour avertir l’utilisateur que l’attachement au processus n’est pas sécurisé.
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7466d88be9460a2b4680fc7d14a741df9238ea0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076262"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` est implémenté par un fournisseur de ports pour avertir l’utilisateur que l’attachement au processus n’est pas sécurisé.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProcessSecurity` .

|Méthode|Description|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtient le nom d’utilisateur du fournisseur de port.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Avertit un utilisateur que l’attachement au processus de débogage n’est pas sécurisé.|

## <a name="remarks"></a>Notes
 Implémentez cette interface pour afficher un avertissement et autoriser l’utilisateur à annuler si le processus auquel vous vous attachez peut être considéré comme non sécurisé.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Ports](../../../extensibility/debugger/ports.md)
- [Fournisseurs de ports](../../../extensibility/debugger/port-suppliers.md)
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
