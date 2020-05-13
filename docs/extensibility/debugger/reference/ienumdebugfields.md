---
title: IEnumDebugFields - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716780"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Cette interface représente une collection d’objets implémentant l’interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par le fournisseur de symboles pour fournir des ensembles d’objets qui implémentent l’interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Notez qu’il ne s’agit pas d’un recensement COM standard en raison de la présence de la méthode [GetCount.](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est retournée par [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) et [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Récupère le prochain ensemble d’objets [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de l’énumération.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Passe un nombre précis d’entrées.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Réinitialise l’énumération à la première entrée.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Récupère une copie de l’énumération actuelle.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Récupère le nombre d’entrées dans le recensement.|

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
