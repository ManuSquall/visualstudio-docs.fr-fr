---
title: 'IDebugProgram2 :: étape | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387224"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Exécute une étape.  
  
> [!NOTE]
> Cette méthode est déconseillée. Utilisez plutôt la méthode [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThread`  
 dans Objet [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread en cours d’exécution pas à pas.  
  
 `sk`  
 dans Valeur de l’énumération [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) qui spécifie le type d’étape.  
  
 `step`  
 dans Valeur de l’énumération [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) qui spécifie l’unité de l’étape (par exemple, par instruction ou instruction).  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 En cas de synchronisation de threads ou de communication entre les threads, les autres threads du programme doivent s’exécuter quand un thread particulier s’exécute pas à pas.  
  
> [!WARNING]
> N’envoyez pas d’événement d’arrêt ou d’événement immédiat (synchrone) à un [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lors de la gestion de cet appel ; dans le cas contraire, le débogueur peut cesser de répondre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
