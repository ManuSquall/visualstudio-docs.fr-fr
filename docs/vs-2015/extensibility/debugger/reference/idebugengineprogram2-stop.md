---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb74cb2940a91bbc64fa4a06f28d07a828357fc6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952549"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Arrête tous les threads en cours d’exécution dans ce programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
