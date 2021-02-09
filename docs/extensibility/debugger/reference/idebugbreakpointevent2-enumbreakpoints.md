---
title: 'IDebugBreakpointEvent2 :: EnumBreakpoints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaf3cac6d49ef2d09a9952ac41b2bb36262fbc7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899037"
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
Crée un énumérateur pour tous les points d’arrêt qui ont été déclenchés à l’emplacement de code actuel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumBreakpoints(
  IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBreakpoints(
  out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
à Retourne un objet [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) qui énumère tous les points d’arrêt associés à l’emplacement de code actuel.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Tous les points d’arrêt d’un emplacement particulier ne peuvent pas être activés à un moment donné (par exemple, un point d’arrêt avec une condition ne se déclenche pas tant que cette condition n’est pas remplie).

## <a name="see-also"></a>Voir aussi
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
