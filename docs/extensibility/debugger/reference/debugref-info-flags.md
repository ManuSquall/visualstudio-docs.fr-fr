---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "Énumération de DEBUGREF_INFO_FLAGS"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer à propos d'un objet de référence de débogage.  
  
## Syntaxe  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## Membres  
 DEBUGREF\_INFORMATION\_NAME  
 Initialisez\/utilisez le champ d' `bstrName` dans la structure.  
  
 DEBUGREF\_INFORMATION\_TYPE  
 Initialisez\/utilisez le champ d' `bstrType` dans la structure.  
  
 DEBUGREF\_INFORMATION\_VALUE  
 Initialisez\/utilisez le champ d' `bstrValue` dans la structure.  
  
 DEBUGREF\_INFORMATION\_ATTRIB  
 Initialisez\/utilisez le champ d'`dwAttrib` dans la structure.  
  
 DEBUGREF\_INFORMATION\_REFTYPE  
 Initialisez\/utilisez le champ d' `dwRefType` dans la structure.  
  
 DEBUGREF\_INFORMATION\_REF  
 Initialisez\/utilisez le champ d' `pReference` dans la structure.  
  
 DEBUGREF\_INFORMATION\_VALUE\_AUTOEXPAND  
 Le champ de valeur doit contenir la valeur automobile\-développée, si disponible, pour ce type d'objet.  
  
 DEBUGREF\_INFORMATION\_NONE  
 Indique qu'aucun indicateur n'est défini.  
  
 DEBUGREF\_INFORMATION\_ALL  
 Indique un masque les balises.  
  
## Notes  
 Ces indicateurs sont passées aux méthodes d' [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) et d' [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) pour indiquer que des champs de la structure de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) doivent être initialisé.  
  
 Utilisé pour le membre d' `dwFields` de la structure d' `DEBUG_REFERENCE_INFO` pour indiquer les champs sont utilisés et valide lorsque la structure est retournée.  
  
 Ces valeurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)