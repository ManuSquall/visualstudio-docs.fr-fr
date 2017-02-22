---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "Énumération de CONTEXT_INFO_FIELDS"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer à propos d'un contexte de mémoire.  
  
## Syntaxe  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## Membres  
 CIF\_MODULEURL  
 Initialisez\/utilisez le champ d' `bstrModuleUrl` de la structure de [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) .  
  
 CIF\_FUNCTION  
 Initialisez\/utilisez le champ d' `bstrFunction` de la structure d' `CONTEXT_INFO` .  
  
 CIF\_FUNCTIONOFFSET  
 Initialisez\/utilisez le champ d' `posFunctionOffset` de la structure d' `CONTEXT_INFO` .  
  
 CIF\_ADDRESS  
 Initialisez\/utilisez le champ d' `bstrAddress` de la structure d' `CONTEXT_INFO` .  
  
 CIF\_ADDRESSOFFSET  
 Initialisez\/utilisez le champ d' `bstrAddressOffset` de la structure d' `CONTEXT_INFO` .  
  
 CIF\_ALLFIELDS  
 Initialisez\/utiliser tous les champs de la structure d' `CONTEXT_INFO` .  
  
## Notes  
 Ces valeurs sont passées à un paramètre la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) pour indiquer que les champs de la structure de [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) doivent être initialisé.  
  
 Ces indicateurs sont également utilisées pour indiquer que les champs de la structure d' `CONTEXT_INFO` sont utilisés et valides lorsque la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec une opération de bits OR.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)