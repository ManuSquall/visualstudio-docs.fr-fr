---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b31efd42d4d51384a09d6f0468484561e32f4397
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944815"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Cette interface fournit l’accès à l’ID du processus qui possède l’objet dont l’adresse est représentée par cette interface.

## <a name="syntax"></a>Syntaxe

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface sur le même objet qui implémente l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Cette interface fournit l’accès à l’ID du processus qui possède l’objet associé à cette adresse.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 En plus des méthodes héritées de l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Récupère l’ID du processus qui possède l’objet représenté par cette interface.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
