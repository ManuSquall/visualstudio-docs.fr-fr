---
title: IDebugExceptionEvent2::PassToDebuggee Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729834"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Précise si l’exception doit être transmise au programme qui est débogé lorsque l’exécution reprend, ou si l’exception doit être écartée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Paramètres
`fPass`\
[dans] Nonzero`TRUE`( ) si l’exception doit être transmise au programme étant déboisé lorsque l’exécution reprend, ou zéro (`FALSE`) si l’exception doit être écartée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’appel de cette méthode ne provoque pas réellement un code à être exécuté dans le programme d’être débogé. L’appel est simplement de définir l’État pour la prochaine exécution du code. Par exemple, les appels à la méthode [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) peuvent revenir `S_OK` avec le [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` champ mis `EXCEPTION_STOP_SECOND_CHANCE`à .

 L’IDE peut recevoir [l’événement IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) et appeler la méthode [Continuer.](../../../extensibility/debugger/reference/idebugprogram2-continue.md) Le moteur de débogé (DE) doit avoir un `PassToDebuggee` comportement par défaut pour traiter le cas si la méthode n’est pas appelée.

## <a name="see-also"></a>Voir aussi
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
