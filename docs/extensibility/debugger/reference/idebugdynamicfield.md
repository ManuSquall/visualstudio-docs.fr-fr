---
title: IDebugDynamicField - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731315"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Cette interface représente un type de variable.

## <a name="syntax"></a>Syntaxe

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par les fournisseurs de symboles comme classe de base pour tout type qui peut être déterminé au moment de l’exécution. C’est pour le code géré seulement.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface représente une classe de base à partir de laquelle des interfaces plus spécialisées peuvent être dérivées.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface ne fournit pas d’autres méthodes que celles héritées de `IDebugField`.

## <a name="requirements"></a>Spécifications
 En-tête: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
