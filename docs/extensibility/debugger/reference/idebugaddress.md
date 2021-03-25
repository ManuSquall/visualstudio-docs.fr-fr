---
description: Cette interface représente l’adresse d’un élément.
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89e192f61e4cda809e8e6c90106cbe081392a044
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094417"
---
# <a name="idebugaddress"></a>IDebugAddress
Cette interface représente l’adresse d’un élément. Elle est retournée par le gestionnaire de symboles.

## <a name="syntax"></a>Syntaxe

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface pour représenter une adresse d’un objet.

## <a name="notes-for-callers"></a>Notes pour les appelants
 De nombreuses méthodes sur de nombreuses interfaces retournent cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Récupère une structure de [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) décrivant un objet et son emplacement.|

## <a name="remarks"></a>Notes
 Le fournisseur de symboles retourne cette interface pour représenter un objet et son emplacement dans une portée particulière (par exemple, une fonction, une méthode ou une classe). Cette interface est retournée à partir de et passée à différentes méthodes du fournisseur de symboles et de l’évaluateur d’expression. Normalement, le fournisseur de symboles est la seule entité qui doit interpréter le contenu de cette interface.

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
