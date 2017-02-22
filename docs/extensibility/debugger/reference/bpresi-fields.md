---
title: "BPRESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "Énumération de BPRESI_FIELDS"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer sur la correction effective d'un point d'arrêt.  
  
## Syntaxe  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## Membres  
 BPRESI\_BPRESLOCATION  
 Initialisez\/utilisez le champ d' `bpResLocation` \(emplacement de résolution de point d'arrêt\) de la structure de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .  
  
 BPRESI\_PROGRAM  
 Initialisez\/utilisez le champ d' `pProgram` de la structure d' `BP_RESOLUTION_INFO` .  
  
 BPRESI\_THREAD  
 Initialisez\/utilisez le champ d' `pThread` de la structure d' `BP_RESOLUTION_INFO` .  
  
 BPRESI\_ALLFIELDS  
 spécifie tous les champs.  
  
## Notes  
 passé à la méthode d' [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) indiquer que des champs de la structure de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) doivent être initialisé.  
  
 Ces indicateurs sont également utilisées pour indiquer que les champs de la structure d' `BP_RESOLUTION_INFO` sont utilisés et valides lorsque cette structure est retournée.  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)