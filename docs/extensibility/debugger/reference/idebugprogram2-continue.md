---
description: 'IDebugProgram2 :: continue poursuit l’exécution de ce programme à partir d’un état arrêté. Tout état d’exécution précédent (par exemple, une étape) est préservé et le programme recommence à s’exécuter.'
title: 'IDebugProgram2 :: continuer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60f3cb4764a53d359e971020df8261d064c62e81
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076119"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Poursuit l’exécution de ce programme à partir d’un état arrêté. Tout état d’exécution précédent (par exemple, une étape) est préservé et le programme recommence à s’exécuter.

> [!NOTE]
> Cette méthode est déconseillée. Utilisez la méthode [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) à la place.

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
`pThread` dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée sur ce programme indépendamment du nombre de programmes en cours de débogage, ou du programme qui a généré l’événement d’arrêt. L’implémentation doit conserver l’état d’exécution précédent (par exemple, une étape) et continuer l’exécution comme si elle n’avait jamais été arrêtée avant la fin de son exécution. Autrement dit, si un thread de ce programme effectue une opération de pas à pas et s’est arrêté en raison de l’arrêt d’un autre programme, puis que cette méthode a été appelée, le programme doit terminer l’opération de pas à pas d’origine.

> [!WARNING]
> N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à un [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors de la gestion de cet appel ; dans le cas contraire, le débogueur peut cesser de répondre.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
