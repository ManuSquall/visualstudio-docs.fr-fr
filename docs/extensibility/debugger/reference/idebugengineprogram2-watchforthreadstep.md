---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5381cff406e3b6e182a6ecbb191381061fb3758
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710381"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Surveille l’exécution (ou cesse de surveiller l’exécution) se produise sur le thread donné.

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

#### <a name="parameters"></a>Paramètres
 `pOriginatingProgram`

 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet représentant le programme en cours en escalier.

 `dwTid`

 [in] Spécifie l’identificateur du thread à surveiller.

 `fWatch`

 [in] Valeur différente de zéro (`TRUE`) moyen de visualiser la présentation pour l’exécution sur le thread identifié par `dwTid`; sinon, zéro (`FALSE`) signifie arrêter d’analyser pour l’exécution sur `dwTid`.

 `dwFrame`

 [in] Spécifie un index de frame qui contrôle le type d’étape. Lorsqu’il s’agit valeur est zéro (0), le type d’étape est « détaillé » et le programme doit s’arrêter dès que le thread identifié par `dwTid` s’exécute. Lorsque `dwFrame` est différente de zéro, le type d’étape est « pas à pas principal » et le programme doit s’arrêter uniquement si le thread identifié par `dwTid` est en cours d’exécution dans un frame dont l’index est égale ou supérieure sur la pile à `dwFrame`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Lorsque le Gestionnaire de session de débogage (SDM) étapes un programme, identifié par le `pOriginatingProgram` paramètre, il avertit tous les autres programmes attachés en appelant cette méthode.

 Cette méthode s’applique uniquement à l’exécution pas à pas du même thread.

## <a name="see-also"></a>Voir aussi
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)