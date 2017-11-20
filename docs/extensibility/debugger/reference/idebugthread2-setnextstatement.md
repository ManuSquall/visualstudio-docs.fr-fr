---
title: IDebugThread2::SetNextStatement | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::SetNextStatement
helpviewer_keywords: IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6dd345fe298af42a69ac076bf92de7df9db82ec2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Définit le pointeur d’instruction en cours pour le contexte de code donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStackFrame`  
 Réservé à un usage ultérieur ; définir une valeur null.  
  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet qui décrit l’emplacement du code sur le point d’être exécutée et son contexte.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant répertorie les autres valeurs possibles.  
  
|Valeur|Description|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|L’instruction next ne peut pas être dans un frame de pile plus approfondie sur le frame de pile.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|L’instruction suivante n’est pas associée à n’importe quelle image dans la pile.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Certains moteurs de débogage ne peut pas définir l’instruction suivante après une exception.|  
  
## <a name="remarks"></a>Remarques  
 Le pointeur d’instruction indique l’instruction ou l’instruction suivante à exécuter. Cette méthode est utilisée pour retenter une ligne de code source ou pour forcer l’exécution dans une autre fonction, par exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)