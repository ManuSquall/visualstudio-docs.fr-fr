---
title: "JMC_CODE_SPEC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "JMC_CODE_SPEC"
helpviewer_keywords: 
  - "Structure JMC_CODE_SPEC"
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# JMC_CODE_SPEC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette structure est utilisée pour définir les informations de JustMyCode pour un module.  
  
## Syntaxe  
  
```cpp#  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```c#  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## Membres  
 fIsUserCode  
 Différente de zéro \(`TRUE`\) si le module doit être étudié le code utilisateur ; sinon, le zéro \(`FALSE`\) si le module doit être traité comme code externe et ne pas être débogué.  
  
 bstrModuleName  
 nom du module en question.  
  
## Notes  
 Cette structure est passée comme une liste de telles structures à la méthode d' [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)