---
title: IDebugProgram2::CauseBreak | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::CauseBreak
helpviewer_keywords: IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a58abdcf816896c0705a7ecce32ae82c9c8f16d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Les demandes que le programme s’arrêter l’exécution de la prochaine heure à laquelle un de ses tentatives de threads d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Un [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) événement est envoyé lorsque le programme tente ensuite d’exécuter du code une fois que cette méthode est appelée.  
  
 Cette méthode est asynchrone, la méthode retourne immédiatement sans nécessairement attendre l’arrêt du programme.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)