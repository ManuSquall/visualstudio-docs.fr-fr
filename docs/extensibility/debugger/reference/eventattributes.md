---
title: ÉVÉNEMENTSATTRIBUTES Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737064"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Spécifie les attributs de l’événement.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Champs
`EVENT_ASYNCHRONOUS`\
Indique que l’événement est asynchrone et aucune réponse à l’événement n’est nécessaire.

`EVENT_SYNCHRONOUS`\
Indique que l’événement est synchrone; réponse au moyen de [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indique qu’il s’agit d’un événement d’arrêt. Doit être combiné `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`avec l’un ou l’autre ou .

`EVENT_ASYNC_STOP`\
Indique un événement d’arrêt asynchrone. Il n’y a actuellement aucun événement de ce genre. Ce drapeau n’est qu’un lieu réservé.

`EVENT_SYNC_STOP`\
Indique un événement d’arrêt synchrone (une combinaison de `EVENT_SYNCHRONOUS` et `EVENT_STOPPING`). Cette valeur est utilisée par un moteur de débogé (DE) lorsqu’il envoie un événement d’arrêt. La réponse est faite au moyen d’un appel à [exécuter](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Étape](../../../extensibility/debugger/reference/idebugprogram2-step.md), ou [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indique un événement qui est envoyé immédiatement et en synchrone à l’IDE. Ce drapeau est combiné `EVENT_ASYNCHRONOUS`avec `EVENT_SYNCHRONOUS`d’autres drapeaux comme , , ou `EVENT_SYNC_STOP` pour indiquer le type d’événement et le fait que le mécanisme de réponse (le cas échéant) est connu.

`EVENT_EXPRESSION_EVALUATION`\
L’événement est le résultat de l’évaluation de l’expression.

## <a name="remarks"></a>Notes
Ces valeurs sont `dwAttrib` transmises dans le paramètre de la méthode [De l’Événement.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

Ces valeurs peuvent être combinées avec un peu plus. `OR`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
