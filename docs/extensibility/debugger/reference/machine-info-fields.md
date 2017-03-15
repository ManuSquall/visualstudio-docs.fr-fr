---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "Énumération de MACHINE_INFO_FIELDS"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type d'informations à récupérer un pour un ordinateur particulier.  
  
## Syntaxe  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## Membres  
 MCIF\_NAME  
 Initialisez\/utilisez le champ d' `bstrName` dans la structure.  
  
 MCIF\_FLAGS  
 Initialisez\/utilisez le champ d' `Flags` dans la structure.  
  
 MIF\_ALL  
 Initialisez\/utiliser tous les champs de la structure.  
  
## Notes  
 Ces valeurs sont passées à la méthode d' [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) pour indiquer que les membres de la structure de [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) doivent être initialisé.  
  
 Également utilisé dans le membre d' `Fields` de la structure d' `MACHINE_INFO` pour indiquer les champs sont utilisés et valides.  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)