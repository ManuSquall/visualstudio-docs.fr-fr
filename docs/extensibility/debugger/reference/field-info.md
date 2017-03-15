---
title: "FIELD_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO"
helpviewer_keywords: 
  - "Structure FIELD_INFO"
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette structure décrit une variable locale, le paramètre, ou un autre champ.  
  
## Syntaxe  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## Membres  
 dwFields  
 Une combinaison des indicateurs d'énumération de [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) qui spécifie quels membres sont terminés.  
  
 bstrFullName  
 le nom complet du champ.  
  
 bstrName  
 le nom court du champ.  
  
 bstrType  
 Type du champ.  
  
 dwModifiers  
 Une combinaison des indicateurs d'énumération de [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) qui décrit le champ.  
  
## Notes  
 Cette structure est passée à la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) où elle est terminée.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)