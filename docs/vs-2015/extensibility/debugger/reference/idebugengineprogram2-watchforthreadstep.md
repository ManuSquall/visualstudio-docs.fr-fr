---
title: 'IDebugEngineProgram2 :: WatchForThreadStep | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59489af368c2e95a2d3cc93edbd6f7ab02a1c156
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195654"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Surveille l’exécution (ou arrête la surveillance de l’exécution) sur le thread donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 dans Objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) représentant le programme en cours d’exécution en escalier.  
  
 `dwTid`  
 dans Spécifie l’identificateur du thread à surveiller.  
  
 `fWatch`  
 dans Une valeur différente de zéro ( `TRUE` ) signifie que commence à surveiller l’exécution sur le thread identifié par `dwTid` ; sinon, zéro ( `FALSE` ) signifie arrêter la surveillance de l’exécution sur `dwTid` .  
  
 `dwFrame`  
 dans Spécifie un index de frame qui contrôle le type d’étape. Quand la valeur est égale à zéro (0), le type d’étape est « pas à pas détaillé » et le programme doit s’arrêter chaque fois que le thread identifié par `dwTid` s’exécute. Lorsque `dwFrame` est différent de zéro, le type d’étape est « pas à pas principal » et le programme doit s’arrêter uniquement si le thread identifié par `dwTid` s’exécute dans un frame dont l’index est supérieur ou égal à la pile `dwFrame` .  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Quand le gestionnaire de débogage de session (SDM) suit un programme, identifié par le `pOriginatingProgram` paramètre, il notifie tous les autres programmes attachés en appelant cette méthode.  
  
 Cette méthode s’applique uniquement au pas à pas du même thread.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
