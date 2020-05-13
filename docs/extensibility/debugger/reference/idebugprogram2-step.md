---
title: IDebugProgram2::Étape Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722756"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Effectue une étape.

> [!NOTE]
> Cette méthode est déconseillée. Utilisez la méthode [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Paramètres
`pThread`\
[dans] Un objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le fil en train d’être mis à l’avant.

`sk`\
[dans] Une valeur de l’énumération [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) qui spécifie le genre d’étape.

`step`\
[dans] Une valeur du recensement [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) qui spécifie l’unité d’étape (par exemple, par déclaration ou instruction).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Dans le cas où il ya une synchronisation de thread ou de communication entre les threads, d’autres threads dans le programme doit s’exécuter quand un thread particulier est en marche.

> [!WARNING]
> N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à [l’événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) pendant le traitement de cet appel; sinon le débbuggeur peut accrocher.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
