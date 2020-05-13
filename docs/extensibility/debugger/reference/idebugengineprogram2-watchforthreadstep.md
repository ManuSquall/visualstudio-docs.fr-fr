---
title: IDebugEngineProgram2::WatchForThreadStep ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730357"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Montres pour l’exécution (ou cesse de regarder pour l’exécution) de se produire sur le fil donné.

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
[dans] Un objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) représentant le programme en cours d’étapes.

`dwTid`\
[dans] Spécifie l’identifiant du fil à regarder.

`fWatch`\
[dans] Non-zéro`TRUE`( ) signifie commencer à regarder `dwTid`pour l’exécution sur le fil identifié par ; autrement, zéro`FALSE`( ) signifie `dwTid`arrêter de regarder pour l’exécution sur .

`dwFrame`\
[dans] Spécifie un index de trame qui contrôle le type d’étape. Lorsque cette valeur est nulle (0), le type d’étape est "étape `dwTid` dans" et le programme doit s’arrêter chaque fois que le thread identifié par exécute. Quand `dwFrame` est non-zéro, le type d’étape est "étape plus" `dwTid` et le programme ne doit s’arrêter que `dwFrame`si le thread identifié par est en cours d’exécution dans un cadre dont l’index est égal ou supérieur sur la pile que .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Lorsque le gestionnaire de déboiffé de session (SDM) étapes d’un programme, identifié par le `pOriginatingProgram` paramètre, il informe tous les autres programmes ci-joints en appelant cette méthode.

 Cette méthode ne s’applique qu’à la marche du même fil.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
