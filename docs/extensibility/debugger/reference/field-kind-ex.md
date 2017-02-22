---
title: "FIELD_KIND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Énumération de FIELD_KIND_EX"
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Énumère les types supplémentaires de champs et un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) peut contenir.  cette énumération étend l'énumération de [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) .  
  
## Syntaxe  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```c#  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## Membres  
 FIELD\_KIND\_EX\_NONE  
 Le champ ne contient pas de type étendu.  
  
 FIELD\_TYPE\_EX\_METHODVAR  
 le champ contient une variable de méthode.  
  
 FIELD\_TYPE\_EX\_CLASSVAR  
 le champ contient une variable de classe.  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)