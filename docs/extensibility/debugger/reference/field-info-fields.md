---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "Énumération de FIELD_INFO_FIELDS"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les informations à récupérer sur un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Syntaxe  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## Membres  
 FIF\_FULLNAME  
 Initialisez\/utilisez le champ d' `bstrFullName` dans la structure de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
 FIF\_NAME  
 Initialisez\/utilisez le champ d' `bstrName` dans la structure d' `FIELD_INFO` .  
  
 FIF\_TYPE  
 Initialisez\/utilisez le champ d' `bstrType` dans la structure d' `FIELD_INFO` .  
  
 FIF\_MODIFIERS  
 Initialisez\/utilisez le champ d' `bstrModifiers` dans la structure d' `FIELD_INFO` .  
  
## Notes  
 Ces valeurs sont également passées comme un argument à la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pour spécifier les champs de la structure de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) doivent être initialisé.  
  
 Ces valeurs sont également utilisées dans le membre d' `dwFields` de la structure d' `FIELD_INFO` pour indiquer les champs sont utilisés et valides.  
  
 Ces indicateurs peuvent être combinées avec `OR`de bits.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)