---
title: IDebugPortSupplier3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724443"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Cette interface permet à un appelant de déterminer si un fournisseur de ports peut préserver les ports (en les écrivant au disque) entre les invocations du débbuggeur, puis obtenir une liste de ces ports préservés.

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour prendre en charge les informations portuaires persistantes ou d’économie sur disque. Cette interface doit être implémentée sur le même objet que l’interface [IDebugPortSupplier2.](../../../extensibility/debugger/reference/idebugportsupplier2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` sur l’interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 En plus des méthodes héritées de l’interface [IDebugPortSupplier2,](../../../extensibility/debugger/reference/idebugportsupplier2.md) cette interface prend en charge ce qui suit :

|Méthode|Description|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retourne si le fournisseur de port peut persister ports (en les écrivant au disque) entre les invocations du débbugger.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Renvoie un objet qui peut être utilisé pour énumérer à travers tous les ports qui ont été écrits sur disque par ce fournisseur de port.|

## <a name="remarks"></a>Notes
 Si un fournisseur portuaire peut persister dans les ports à travers les invocations, il doit implémenter cette interface. Les ports doivent être chargés lorsque le fournisseur du port est instantané et écrits sur disque lorsque le fournisseur du port est détruit.

 Un moteur de débogé ne va généralement pas interagir avec un fournisseur de port et n’aura aucune utilité pour cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
