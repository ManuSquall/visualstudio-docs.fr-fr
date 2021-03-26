---
description: Cette interface représente une collection d’objets qui implémentent l’interface IDebugAddress.
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29b927f9b614e95be51bd285e36ab1e01c09f568
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083126"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Cette interface représente une collection d’objets qui implémentent l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="syntax"></a>Syntaxe

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par le fournisseur de symboles pour fournir des ensembles d’objets qui implémentent l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) . Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la méthode [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 Cette interface implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Récupère le jeu d’objets [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) suivant de l’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignore un nombre spécifié d’entrées.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Rétablit la première entrée de l’énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Récupère une copie de l’énumération actuelle.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|

## <a name="remarks"></a>Notes
 Cette interface est généralement utilisée par le moteur de débogage pour aider à déterminer l’adresse appropriée à attribuer à l’évaluateur d’expression.

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
