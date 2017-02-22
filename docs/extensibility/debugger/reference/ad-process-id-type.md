---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "Énumération de AD_PROCESS_ID_TYPE"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie comment interpréter un ID de processus dans la structure d' [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
## Syntaxe  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## Membres  
 AD\_PROCESS\_ID\_SYSTEM  
 l'ID de processus est un identificateur système.  utilisez le champ d' `ProcessId.dwProcessId` de la structure d' [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
 AD\_PROCESS\_ID\_GUID  
 L'ID de processus est un GUID.  utilisez le champ d' `ProcessId.guidProcessId` de la structure d' `AD_PROCESS_ID` .  
  
## Notes  
 Utilisé pour le membre d' `ProcessIdType` de la structure d' [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) pour identifier le type d'ID de processus contenu dans la structure.  détermine comment interpréter l'union d' `ProcessId` dans la structure.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)