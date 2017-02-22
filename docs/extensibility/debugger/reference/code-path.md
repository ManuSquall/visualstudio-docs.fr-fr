---
title: "CODE_PATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CODE_PATH"
helpviewer_keywords: 
  - "Structure CODE_PATH"
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CODE_PATH
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit un appel de méthode ou de fonction.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```c#  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## Membres  
 bstrName  
 le nom du chemin de code.  
  
 pCode  
 L'objet d' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) qui identifie l'endroit du code accéder à une fonction.  
  
## Notes  
 cette structure est utilisée pour implémenter la progression dans une fonction.  [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) retourne tous les appels de la position actuelle dans le programme débogué.  Cette structure représente un appel.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)