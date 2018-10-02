---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d67290ea7bf88f8cdf01e88444cd69ec25d73a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494984"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugEngineProgram2::WatchForExpressionEvaluationOnThread](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread).  
  
Autorise (ou interdit) d’évaluation d’expression se produise sur le thread donné, même si le programme s’est arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pOriginatingProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet représentant le programme qui évalue une expression.  
  
 `dwTid`  
 [in] Spécifie l’identificateur du thread.  
  
 `dwEvalFlags`  
 [in] Une combinaison d’indicateurs de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) énumération qui spécifient la façon dont l’évaluation doit être effectuée.  
  
 `pExprCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet à utiliser pour envoyer des événements de débogage qui se produisent pendant l’évaluation d’expression.  
  
 `fWatch`  
 [in] Si non nulle (`TRUE`), permet l’évaluation de l’expression sur le thread identifié par `dwTid`; sinon, zéro (`FALSE`) n’autorise pas d’évaluation de l’expression sur ce thread.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Lorsque le Gestionnaire de session de débogage (SDM) demande un programme, identifié par le `pOriginatingProgram` paramètre, pour évaluer une expression, il avertit tous les autres programmes attachés en appelant cette méthode.  
  
 Évaluation des expressions dans un programme peut entraîner le code à exécuter dans un autre, en raison d’une version d’évaluation de fonction ou de n’importe quel `IDispatch` propriétés. Pour cette raison, cette méthode permet d’évaluation d’expression exécuter et terminer même si le thread peut être arrêté dans ce programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

