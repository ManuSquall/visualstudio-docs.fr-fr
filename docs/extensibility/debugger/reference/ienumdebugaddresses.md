---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f7871a223695632b5c2118377c9cfeb24d297e4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329918"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Cette interface représente une collection d’objets qui implémentent le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par le fournisseur de symboles pour fournir des jeux d’objets qui implémentent le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) (méthode).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Récupère l’ensemble suivant de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objets à partir de l’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignore un nombre spécifié d’entrées.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Réinitialise l’énumération à la première entrée.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Récupère une copie de l’énumération actuelle.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|

## <a name="remarks"></a>Notes
 Cette interface est généralement utilisée par le moteur de débogage pour aider à déterminer l’adresse appropriée afin de donner à l’évaluateur d’expression.

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)