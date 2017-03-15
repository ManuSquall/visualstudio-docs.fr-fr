---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "Énumération de PROCESS_INFO_FIELDS"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifié le type d'informations à récupérer pour un processus.  
  
## Syntaxe  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## Membres  
 PIF\_FILE\_NAME  
 Initialisez\/utilisez le champ d' `bstrFileName` de la structure de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 PIF\_BASE\_NAME  
 Initialisez\/utilisez le champ d' `bstrBaseName` de la structure d' `PROCESS_INFO` .  
  
 PIF\_TITLE  
 Initialisez\/utilisez le champ d' `bstrTitle` de la structure d' `PROCESS_INFO` .  
  
 PIF\_PROCESS\_ID  
 Initialisez\/utilisez le champ d' `ProcessId` de la structure d' `PROCESS_INFO` .  
  
 PIF\_SESSION\_ID  
 Initialisez\/utilisez le champ d' `dwSessionId` de la structure d' `PROCESS_INFO` .  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 Initialisez\/utilisez le champ d' `bstrAttachedSessionName` de la structure d' `PROCESS_INFO` .  
  
 PIF\_CREATION\_TIME  
 Initialisez\/utilisez le champ d' `CreationTime` de la structure d' `PROCESS_INFO` .  
  
 PIF\_FLAGS  
 Initialisez\/utilisez le champ d' `Flags` de la structure d' `PROCESS_INFO` .  
  
 PIF\_ALL  
 Effectue tous les champs.  
  
## Notes  
 passé à la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) indiquer que des champs de la structure de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) doivent être initialisé.  
  
 Également utilisé dans le domaine de `Fields` de la structure d' `PROCESS_INFO` pour indiquer les champs sont utilisés et valides.  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)