---
title: IDebugEngineProgram2::Stop | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab5bec65dc3f53681d40743bea694295ff69944b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Arrête tous les threads en cours d’exécution dans ce programme.  
  
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
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque ce programme est en cours de débogage dans un environnement de programme multiples. Lorsqu’un événement d’arrêt à partir d’un autre programme est reçu, cette méthode est appelée sur ce programme. L’implémentation de cette méthode doit être asynchrone ; Autrement dit, pas tous les threads doivent être doit être arrêté avant le retour de cette méthode. L’implémentation de cette méthode peut être aussi simple que d’appeler le [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) méthode sur ce programme.  
  
 Aucun événement de débogage est envoyé en réponse à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)