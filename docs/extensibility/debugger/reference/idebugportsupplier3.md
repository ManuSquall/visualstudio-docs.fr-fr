---
description: Cette interface permet à un appelant de déterminer si un fournisseur de ports peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur, puis obtenir la liste de ces ports conservés.
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8db7c2321d5a309f66b85a3f177e20cb3f9b1244
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150391"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Cette interface permet à un appelant de déterminer si un fournisseur de ports peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur, puis obtenir la liste de ces ports conservés.

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour prendre en charge la persistance ou l’enregistrement des informations de port sur le disque. Cette interface doit être implémentée sur le même objet que l’interface [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur l' `IDebugPortSupplier2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 Outre les méthodes héritées de l’interface [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , cette interface prend en charge les éléments suivants :

|Méthode|Description|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retourne une valeur indiquant si le fournisseur de ports peut conserver les ports (en les écrivant sur le disque) entre les appels du débogueur.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retourne un objet qui peut être utilisé pour énumérer tous les ports qui ont été écrits sur le disque par ce fournisseur de port.|

## <a name="remarks"></a>Notes
 Si un fournisseur de ports peut conserver des ports entre les appels, il doit implémenter cette interface. Les ports doivent être chargés lorsque le fournisseur de port est instancié et écrits sur le disque lors de la destruction du fournisseur de port.

 En général, un moteur de débogage n’interagit pas avec un fournisseur de port et n’a pas d’utilisation pour cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
