---
description: Spécifie les attributs d’événement.
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 922c60c0bb36c58b88c2422580eeda0db1c02d42
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059481"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Spécifie les attributs d’événement.

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
Indique que l’événement est asynchrone et qu’aucune réponse à l’événement n’est nécessaire.

`EVENT_SYNCHRONOUS`\
Indique que l’événement est synchrone ; répondre au moyen de [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indique qu’il s’agit d’un événement d’arrêt. Doit être combiné avec `EVENT_ASYNCHRONOUS` ou `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Indique un événement d’arrêt asynchrone. Il n’existe actuellement aucun événement de ce type. Cet indicateur est uniquement un espace réservé.

`EVENT_SYNC_STOP`\
Indique un événement d’arrêt synchrone (une combinaison de `EVENT_SYNCHRONOUS` et `EVENT_STOPPING` ). Cette valeur est utilisée par un moteur DE débogage (DE) lorsqu’il envoie un événement d’arrêt. La réponse est effectuée au moyen d’un appel à [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)ou [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indique un événement qui est envoyé immédiatement et de façon synchrone à l’IDE. Cet indicateur est combiné avec d’autres indicateurs tels que `EVENT_ASYNCHRONOUS` , `EVENT_SYNCHRONOUS` ou `EVENT_SYNC_STOP` pour indiquer le type d’événement et le fait que le mécanisme de réponse (le cas échéant) est connu.

`EVENT_EXPRESSION_EVALUATION`\
L’événement est un résultat de l’évaluation de l’expression.

## <a name="remarks"></a>Notes
Ces valeurs sont passées dans le `dwAttrib` paramètre de la méthode d' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

Ces valeurs peuvent être combinées avec une opération de bits `OR` .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
