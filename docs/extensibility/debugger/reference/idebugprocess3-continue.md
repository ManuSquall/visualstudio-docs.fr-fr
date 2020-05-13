---
title: IDebugProcess3:Continuer Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723770"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continue à exécuter ce processus à partir d’un état arrêté. Tout état d’exécution précédent (comme une étape) est préservé, et le processus commence à exécuter à nouveau.

> [!NOTE]
> Cette méthode doit être utilisée au lieu de [Continuer](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
[dans] Un objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) représentant le fil à poursuivre.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; autrement, renvoie le code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée sur ce processus indépendamment du nombre de processus sont débogés, ou quel processus a généré l’événement d’arrêt. La mise en œuvre doit conserver l’état d’exécution précédent (comme une étape) et poursuivre l’exécution comme si elle n’avait jamais cessé avant d’achever son exécution antérieure. Autrement dit, si un thread dans ce processus faisait un pas en arrière `Continue` et a été arrêté parce qu’un autre processus arrêté, puis a été appelé, le thread spécifié doit compléter le fonctionnement d’étape d’origine.

 **Avertissement** N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à [l’événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) pendant le traitement de cet appel; sinon le débbuggeur peut accrocher.

## <a name="see-also"></a>Voir aussi
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
