---
title: "PROVIDER_PROCESS_DATA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_PROCESS_DATA"
helpviewer_keywords: 
  - "Structure PROVIDER_PROCESS_DATA"
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette structure fournit des informations sur les processus qui s'exécutent sur un ordinateur.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```c#  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## Membres  
 Champs  
 Une combinaison des indicateurs d'énumération de [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , indiquant les champs sont remplis.  
  
 ProgramNodes  
 Une structure de [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) qui contient un tableau de nœuds du programme.  
  
 fIsDebuggerPresent  
 une valeur différente de zéro \(`TRUE`\) si le débogueur de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] exécute, zéro \(`FALSE`\) s'il n'est pas.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) où elle est terminée.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)