---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66fd149bc3eed7633586c156f6493c8febcbeaac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330361"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Cette interface fournit l’accès à l’ID du processus qui possède l’objet dont l’adresse est représentée par cette interface.

## <a name="syntax"></a>Syntaxe

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Cette interface fournit l’accès à l’ID du processus qui possède l’objet qui est associé à cette adresse.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre de vtable
 Outre les méthodes héritées de la [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface, cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Récupère l’ID de processus qui possède l’objet représenté par cette interface.|

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)