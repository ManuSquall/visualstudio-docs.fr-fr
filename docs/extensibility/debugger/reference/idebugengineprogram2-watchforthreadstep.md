---
title: IDebugEngineProgram2::WatchForThreadStep | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords: IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 473deca83bea9e2fea9c52d2836291790def5804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
#### <a name="parameters"></a>Paramètres  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet représentant le programme en cours en retrait.  
  
 `dwTid`  
 [in] Spécifie l’identificateur du thread à surveiller.  
  
 `fWatch`  
 [in] Non nul (`TRUE`) signifie démarrer la surveillance de l’exécution sur le thread identifié par `dwTid`; sinon, zéro (`FALSE`) signifie l’arrêt de la surveillance de l’exécution sur `dwTid`.  
  
 `dwFrame`  
 [in] Spécifie un index de frame qui contrôle le type d’étape. Lorsqu’il s’agit de valeur est zéro (0), le type d’étape est « pas à pas détaillé » et le programme doit s’arrêter dès que le thread identifié par `dwTid` s’exécute. Lorsque `dwFrame` est différente de zéro, le type d’étape est « pas à pas principal » et le programme doit s’arrêter uniquement si le thread identifié par `dwTid` est en cours d’exécution dans un frame dont l’index est égale ou supérieure sur la pile à `dwFrame`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Lorsque le Gestionnaire de session de débogage (SDM) étapes un programme, identifié par le `pOriginatingProgram` paramètre, il avertit tous les autres programmes attachés en appelant cette méthode.  
  
 Cette méthode s’applique uniquement à l’exécution pas à pas du même thread.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)