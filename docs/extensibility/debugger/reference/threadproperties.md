---
title: "THREADPROPERTIES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "Structure THREADPROPERTIES"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit les propriétés d'un thread.  
  
## Syntaxe  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## Membres  
 dwFields  
 Une combinaison des indicateurs d'énumération de [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , décrivant les champs dans cette structure sont valides.  
  
 dwThreadId  
 L'identification du thread  
  
 dwSuspendCount  
 Le compteur de suspension du thread.  
  
 dwThreadState  
 Une valeur de l'énumération de [ÉTATS DU THREAD](../../../extensibility/debugger/reference/threadstate.md) indiquant l'état des threads d'opération.  
  
 bstrPriority  
 une chaîne spécifiant la priorité de thread ; par exemple, « au\-dessus de la normale, » de « normale », ou de « durée critique ».  
  
 bstName  
 le nom de thread.  
  
 bstrLocation  
 L'emplacement de thread \(généralement le frame de pile le plus élevé\), généralement exprimé sous le nom de la méthode où l'exécution est actuellement désactivée.  
  
## Notes  
 Cette structure est effectuée par un appel à la méthode d' [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) .  Les informations donc retournées sont généralement utilisées en remplissant fenêtre de **Threads** .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [ÉTATS DU THREAD](../../../extensibility/debugger/reference/threadstate.md)