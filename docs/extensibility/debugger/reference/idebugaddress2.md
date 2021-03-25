---
description: Cette interface fournit l’accès à l’ID du processus qui possède l’objet dont l’adresse est représentée par cette interface.
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e74833768ed1a287c0dcf3b641b858261c2d661
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059181"
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

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
