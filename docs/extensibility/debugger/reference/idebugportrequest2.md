---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83f70a9fe027f004ef3829827ba8af40f7fb72e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340311"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Cette interface décrit un port. Cette description est utilisée pour ajouter le port à un fournisseur de port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 En général, Visual Studio implémente cette interface en cours de l’obtention d’un port de débogage à partir d’un fournisseur de port.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface est passée à [ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) pour créer un port de débogage. Un appel à [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) renvoie cette interface, qui représente la requête utilisée pour créer le port en premier lieu.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugPortRequest2`.

|Méthode|Description|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtient le nom du port à créer.|

## <a name="remarks"></a>Notes
 En règle générale, un moteur de débogage n’interagit pas avec un fournisseur de port et sera d’aucune utilité pour cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)