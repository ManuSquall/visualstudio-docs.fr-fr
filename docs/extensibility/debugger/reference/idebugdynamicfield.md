---
description: Cette interface représente un type de variable.
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf1d72bfa38e6af0419e696b267699d10340cc68
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094079"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Cette interface représente un type de variable.

## <a name="syntax"></a>Syntaxe

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par les fournisseurs de symboles en tant que classe de base pour tout type pouvant être déterminé au moment de l’exécution. Il s’agit du code managé uniquement.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface représente une classe de base à partir de laquelle des interfaces plus spécialisées peuvent être dérivées.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre vtable
 Cette interface ne fournit pas de méthodes autres que celles héritées de `IDebugField` .

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
