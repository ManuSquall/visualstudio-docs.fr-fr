---
description: Fait en sorte que le processus effectue un pas à pas détaillé d’une instruction ou d’une instruction.
title: 'IDebugProcess3 :: étape | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85df970c073fa2203873733073c5b6b85cabe06
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150131"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Fait en sorte que le processus effectue un pas à pas détaillé d’une instruction ou d’une instruction.

> [!NOTE]
> Cette méthode doit être utilisée à la place de [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Paramètres
`pThread`\
dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) représentant le thread en cours d’exécution en escalier.

`sk`\
dans Une des valeurs [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
dans Une des valeurs [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 En cas de synchronisation de threads ou de communication entre les threads, les autres threads du processus doivent s’exécuter quand un thread particulier s’exécute pas à pas.

 **Avertissement** N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à un [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors de la gestion de cet appel ; dans le cas contraire, le débogueur peut cesser de répondre.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
