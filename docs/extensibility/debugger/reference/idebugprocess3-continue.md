---
description: Poursuit l’exécution de ce processus à partir d’un état arrêté. Tout état d’exécution précédent (par exemple, une étape) est préservé et le processus recommence à s’exécuter.
title: 'IDebugProcess3 :: continuer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11f2d5b652b950976834b8ba18f71a1dc0d1b34c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081579"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Poursuit l’exécution de ce processus à partir d’un état arrêté. Tout état d’exécution précédent (par exemple, une étape) est préservé et le processus recommence à s’exécuter.

> [!NOTE]
> Cette méthode doit être utilisée à la place de [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
`pThread`\
dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread à continuer.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée sur ce processus, quel que soit le nombre de processus en cours de débogage, ou le processus qui a généré l’événement d’arrêt. L’implémentation doit conserver l’état d’exécution précédent (par exemple, une étape) et continuer l’exécution comme si elle n’avait jamais été arrêtée avant la fin de son exécution. Autrement dit, si un thread de ce processus effectue une opération de pas à pas et s’est arrêté parce qu’un autre processus s’est arrêté, puis `Continue` a été appelé, le thread spécifié doit terminer l’opération de pas à pas d’origine.

 **Avertissement** N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à un [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors de la gestion de cet appel ; dans le cas contraire, le débogueur peut cesser de répondre.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
