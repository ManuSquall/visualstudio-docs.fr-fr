---
title: IDebugProgram2:Continuer Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723080"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continue à exécuter ce programme à partir d’un état arrêté. Tout état d’exécution précédent (comme une étape) est préservé, et le programme recommence à exécuter.

> [!NOTE]
> Cette méthode est déconseillée. Utilisez plutôt la méthode [Continuer.](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Paramètres
`pThread`[dans] Un objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le fil.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée sur ce programme, peu importe combien de programmes sont débogés, ou quel programme a généré l’événement d’arrêt. La mise en œuvre doit conserver l’état d’exécution précédent (comme une étape) et poursuivre l’exécution comme si elle n’avait jamais cessé avant d’achever son exécution antérieure. Autrement dit, si un fil dans ce programme faisait une opération de step-over et a été arrêté parce qu’un autre programme arrêté, et puis cette méthode a été appelée, le programme doit compléter l’opération d’étape initiale.

> [!WARNING]
> N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à [l’événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) pendant le traitement de cet appel; sinon le débbuggeur peut accrocher.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
