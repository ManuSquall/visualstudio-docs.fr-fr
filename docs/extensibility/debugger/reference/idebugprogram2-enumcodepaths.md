---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

extrait une liste des chemins de code pour une position donnée dans un fichier source.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### Paramètres  
 `pszHint`  
 \[in\]  Le mot sous le curseur dans la vue de **Source** ou de **Code Machine** dans l'IDE.  
  
 `pStart`  
 \[in\]  un objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) représentant le contexte de code actuel.  
  
 `pFrame`  
 \[in\]  Un objet d' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) représentant le frame de pile associé au point d'arrêt actuel.  
  
 `fSource`  
 \[in\]  Une valeur différente de zéro \(`TRUE`\) si en mode Source, ou zéro \(`FALSE`\) si dans la vue de **Code Machine** .  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) contenant une liste des chemins de code.  
  
 `ppSafety`  
 \[out\]  Retourne un objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) représentant un contexte de code supplémentaire à définir comme point d'arrêt au cas où le chemin de code sélectionné sera ignoré.  Cela peut se produire dans le cas d'une expression booléenne court\-circuitée, par exemple.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un chemin de code décrit le nom d'une méthode ou fonction qui a été appelée pour archiver au point actuel de l'exécution du programme.  une liste de chemins de code représente la pile des appels.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)