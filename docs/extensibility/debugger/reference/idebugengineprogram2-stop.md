---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 089b8c14db3caa1c9f4b3a2ad0a364bcfbb5a096
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840354"
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
 Cette méthode est appelée lorsque ce programme est en cours de débogage dans un environnement de programme multiples. Lorsqu’un événement d’arrêt à partir d’un autre programme est reçu, cette méthode est appelée sur ce programme. L’implémentation de cette méthode doit être asynchrone ; Autrement dit, pas tous les threads doivent être obligatoire doit être arrêtée avant que cette méthode est retournée. L’implémentation de cette méthode peut être aussi simple que si vous appelez le [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) méthode sur ce programme.  
  
 Aucun événement de débogage n’est envoyé en réponse à cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)