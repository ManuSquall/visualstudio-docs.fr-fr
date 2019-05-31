---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d80242ca516c5fa7f3ad297250e25c782664d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350379"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Cette interface représente une collection d’objets qui implémentent le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par le fournisseur de symboles pour fournir des jeux d’objets qui implémentent le [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Notez qu’il ne s’agit pas d’une énumération COM standard en raison de la présence de la [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) (méthode).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface est retournée par [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) et [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Récupère l’ensemble suivant de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objets à partir de l’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Ignore un nombre spécifié d’entrées.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Réinitialise l’énumération à la première entrée.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Récupère une copie de l’énumération actuelle.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Récupère le nombre d’entrées dans l’énumération.|

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)