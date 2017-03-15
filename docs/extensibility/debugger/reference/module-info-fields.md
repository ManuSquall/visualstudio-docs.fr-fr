---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "Énumération de MODULE_INFO_FIELDS"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie des indicateurs pour les informations de module de débogage.  
  
## Syntaxe  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## Membres  
 MIF\_NONE  
 Initialisez\/utilisez aucun des champs de la structure.  
  
 MIF\_NAME  
 Initialisez\/utilisez le champ d' `m_bstrName` dans la structure de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 MIF\_URL  
 Initialisez\/utilisez le champ d' `m_bstrUrl` dans la structure d' `MODULE_INFO` .  
  
 MIF\_VERSION  
 Initialisez\/utilisez le champ d' `m_bstrVersion` dans la structure d' `MODULE_INFO` .  
  
 MIF\_DEBUGMESSAGE  
 Initialisez\/utilisez le champ d' `m_bstrDebugMessage` dans la structure d' `MODULE_INFO` .  
  
 MIF\_LOADADDRESS  
 Initialisez\/utilisez le champ d' `m_addrLoadAddress` dans la structure d' `MODULE_INFO` .  
  
 MIF\_PREFFEREDADDRESS  
 Initialisez\/utilisez le champ d' `m_addrPreferredLoadAddress` dans la structure d' `MODULE_INFO` .  
  
 MIF\_SIZE  
 Initialisez\/utilisez le champ d' `m_dwSize` dans la structure d' `MODULE_INFO` .  
  
 MIF\_LOADORDER  
 Initialisez\/utilisez le champ d' `m_dwLoadOrder` dans la structure d' `MODULE_INFO` .  
  
 MIF\_TIMESTAMP  
 Initialisez\/utilisez le champ d' `m_TimeStamp` dans la structure d' `MODULE_INFO` .  
  
 MIF\_URLSYMBOLLOCATION  
 Initialisez\/utilisez le champ d' `m_bstrUrlSymbolLocation` dans la structure d' `MODULE_INFO` .  
  
 MIF\_FLAGS  
 Initialisez\/utilisez le champ d' `m_dwModuleFlags` dans la structure d' `MODULE_INFO` .  
  
 MIF\_ALLFIELDS  
 Initialisez\/utiliser tous les champs de la structure d' `MODULE_INFO` .  
  
## Notes  
 Ces valeurs sont passées comme un argument à la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) pour indiquer que des champs de la structure de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) doivent être initialisé.  
  
 Ces valeurs sont également utilisées dans la structure d' `MODULE_INFO` pour indiquer les champs sont utilisés et valides.  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)