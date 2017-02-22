---
title: "IDebugProgram2::GetDisassemblyStream | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
helpviewer_keywords: 
  - "IDebugProgram2::GetDisassemblyStream"
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le flux de code machine pour ce programme ou partie de ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```c#  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### Paramètres  
 `dwScope`  
 \[in\]  Spécifie une valeur de l'énumération de [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) qui définit la portée du flux de code machine.  
  
 `pCodeContext`  
 \[in\]  Un objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui représente la position d'où démarrer le flux de code machine.  
  
 `ppDisassemblyStream`  
 \[out\]  Retourne un objet d' [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) qui représente le flux de code machine.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne `E_DISASM_NOTSUPPORTED` si le code machine n'est pas pris en charge pour cette architecture particulière.  
  
## Notes  
 Si le paramètre d' `dwScopes` a la balise d' `DSS_HUGE` de l'énumération de [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) définie, alors il est recommandé que le code machine retourne un grand nombre d'instructions du code machine, par exemple, pour un fichier entier ou un module.  Si la balise d' `DSS_HUGE` n'est pas définie, alors il est recommandé que le code machine est limité à une petite zone, en général qui d'une fonction unique.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY\_STREAM\_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)