---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653d2424d21a18e7053f66e0a74214ecc25d97da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317923"
---
# <a name="idebugaddress"></a>IDebugAddress
Cette interface représente l’adresse d’un élément. Elle est retournée par le Gestionnaire de symboles.

## <a name="syntax"></a>Syntaxe

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un fournisseur de symboles implémente cette interface pour représenter une adresse d’un objet.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 De nombreuses méthodes sur le nombre d’interfaces retournent cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Récupère un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure qui décrit un objet et son emplacement.|

## <a name="remarks"></a>Notes
 Le fournisseur de symboles retourne cette interface pour représenter un objet et son emplacement au sein d’une étendue particulière (par exemple, fonction, méthode ou classe). Cette interface est retournée à partir d’et passée à différentes méthodes de fournisseur de symboles et de l’expression évaluateur. Normalement, le fournisseur de symboles est la seule entité qui a besoin d’interpréter le contenu de cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)