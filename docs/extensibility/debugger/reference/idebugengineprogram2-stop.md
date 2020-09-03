---
title: 'IDebugEngineProgram2 :: Stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730486"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Arrête tous les threads qui s’exécutent dans ce programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée lorsque ce programme est en cours de débogage dans un environnement à plusieurs programmes. Lors de la réception d’un événement d’arrêt d’un autre programme, cette méthode est appelée sur ce programme. L’implémentation de cette méthode doit être asynchrone ; autrement dit, tous les threads ne doivent pas nécessairement être arrêtés avant le retour de cette méthode. L’implémentation de cette méthode peut être aussi simple que l’appel de la méthode [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) sur ce programme.

 Les implémenteurs doivent envoyer un [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) quand le programme s’arrête.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
