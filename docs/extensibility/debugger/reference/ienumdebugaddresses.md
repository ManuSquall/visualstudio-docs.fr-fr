---
title: IEnumDebugAddresses - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717583"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Cette interface représente une collection d’objets implémentant l’interface [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par le fournisseur de symboles pour fournir des ensembles d’objets qui implémentent l’interface [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Notez qu’il ne s’agit pas d’un recensement COM standard en raison de la présence de la méthode [GetCount.](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Récupère le prochain ensemble d’objets [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) de l’énumération.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Passe un nombre précis d’entrées.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Réinitialise l’énumération à la première entrée.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Récupère une copie de l’énumération actuelle.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Récupère le nombre d’entrées dans le recensement.|

## <a name="remarks"></a>Notes
 Cette interface est généralement utilisée par le moteur de débogé pour aider à déterminer l’adresse appropriée à donner à l’évaluateur d’expression.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
