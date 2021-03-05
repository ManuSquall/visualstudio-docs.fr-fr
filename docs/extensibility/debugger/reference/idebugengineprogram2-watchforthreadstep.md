---
description: Surveille l’exécution (ou arrête la surveillance de l’exécution) sur le thread donné.
title: 'IDebugEngineProgram2 :: WatchForThreadStep | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaf02e07bebbbfd711d99ef7605befbdce1f9376
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153415"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Surveille l’exécution (ou arrête la surveillance de l’exécution) sur le thread donné.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Paramètres
`pOriginatingProgram`\
dans Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) représentant le programme en cours d’exécution en escalier.

`dwTid`\
dans Spécifie l’identificateur du thread à surveiller.

`fWatch`\
dans Une valeur différente de zéro ( `TRUE` ) signifie que commence à surveiller l’exécution sur le thread identifié par `dwTid` ; sinon, zéro ( `FALSE` ) signifie arrêter la surveillance de l’exécution sur `dwTid` .

`dwFrame`\
dans Spécifie un index de frame qui contrôle le type d’étape. Quand la valeur est égale à zéro (0), le type d’étape est « pas à pas détaillé » et le programme doit s’arrêter chaque fois que le thread identifié par `dwTid` s’exécute. Lorsque `dwFrame` est différent de zéro, le type d’étape est « pas à pas principal » et le programme doit s’arrêter uniquement si le thread identifié par `dwTid` s’exécute dans un frame dont l’index est supérieur ou égal à la pile `dwFrame` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Quand le gestionnaire de débogage de session (SDM) suit un programme, identifié par le `pOriginatingProgram` paramètre, il notifie tous les autres programmes attachés en appelant cette méthode.

 Cette méthode s’applique uniquement au pas à pas du même thread.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
