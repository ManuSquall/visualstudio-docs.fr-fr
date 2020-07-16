---
title: 'IDebugProgram2 :: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af4650b5523595350543ac549ac162247563e418
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386743"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Poursuit l’exécution de ce programme à partir d’un état arrêté. Tout état d’exécution précédent (par exemple, une étape) est désactivé et le programme recommence à s’exécuter.

> [!NOTE]
> Cette méthode est déconseillée. Utilisez à la place la méthode [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lorsque l’utilisateur commence l’exécution à partir d’un état arrêté dans le thread d’un autre programme, cette méthode est appelée sur ce programme. Cette méthode est également appelée lorsque l’utilisateur sélectionne la commande **Démarrer** dans le menu **Déboguer** de l’IDE. L’implémentation de cette méthode peut être aussi simple que l’appel de la méthode [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) sur le thread actuel dans le programme.

> [!WARNING]
> N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à un [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors de la gestion de cet appel ; dans le cas contraire, le débogueur peut cesser de répondre.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)
