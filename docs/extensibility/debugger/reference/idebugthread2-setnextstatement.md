---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit le pointeur d'instruction actuel au contexte de code donné.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### Paramètres  
 `pStackFrame`  
 Réservé à une utilisation ultérieure ; ensemble à une valeur NULL.  
  
 `pCodeContext`  
 \[in\]  Un objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui décrit l'emplacement du code à environ exécuter et son contexte.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Le tableau suivant montre les autres valeurs possibles.  
  
|Valeur|Description|  
|------------|-----------------|  
|\_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME D'E\_CAN NOT|l'instruction suivante ne peut pas être dans un frame de pile plus profond sur la pile de frame.|  
|\_SETIP\_TO\_DIFFERENT\_FUNCTION D'E\_CAN NOT|L'instruction suivante n'est pas associé à un frame de la pile.|  
|\_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION D'E\_CAN NOT|Des moteurs de débogage ne peuvent pas définir l'instruction suivante après une exception.|  
  
## Notes  
 Le pointeur d'instruction indique l'instruction ou l'instruction suivante à exécuter.  Cette méthode est utilisée pour procéder à une ligne de code source ou pour forcer l'exécution de se poursuivre dans une autre fonction, par exemple.  
  
## Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)