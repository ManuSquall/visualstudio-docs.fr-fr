---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d94a685b9c79069a047e32155234f9bf6a50d5c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875391"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Cette interface représente un type d’une variable.

## <a name="syntax"></a>Syntaxe

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par les fournisseurs de symbole comme classe de base pour tout type qui peut être déterminée au moment de l’exécution. Il s’agit uniquement du code managé.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface représente une classe de base à partir de laquelle des interfaces plus spécialisées peuvent être dérivées.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface ne fournit pas toutes les méthodes autres que celles héritées de `IDebugField`.

## <a name="requirements"></a>Configuration requise
 En-tête : sh.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)