---
title: "MACHINE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO"
helpviewer_keywords: 
  - "Structure MACHINE_INFO"
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# MACHINE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

décrit un ordinateur particulier.  
  
## Syntaxe  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```c#  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## Membres  
 `Fields`  
 Une combinaison des indicateurs d'énumération de [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) qui spécifient que les champs de la structure sont initialisé.  
  
 `bstrName`  
 le nom de l'ordinateur.  Revient à appeler [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Une combinaison des indicateurs d'énumération de [MACHINE\_INFO\_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) décrivant les attributs de l'ordinateur.  
  
## Notes  
 cette structure est retournée par un appel à la méthode d' [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)