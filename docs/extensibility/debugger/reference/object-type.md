---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "Énumération de OBJECT_TYPE"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie le type d'un objet de l'évaluateur d'expression.  
  
## Syntaxe  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## Membres  
 OBJECT\_TYPE\_BOOLEAN  
 Indique que l'objet est une valeur booléenne.  
  
 OBJECT\_TYPE\_CHAR  
 Indique que l'objet est un caractère.  
  
 OBJECT\_TYPE\_I1  
 Indique que l'objet est un entier signé à un octet.  
  
 OBJECT\_TYPE\_U1  
 Indique que l'objet est un entier non signé à un octet.  
  
 OBJECT\_TYPE\_I2  
 indique que l'objet est un entier signé à deux octets.  
  
 OBJECT\_TYPE\_U2  
 Indique que l'objet est un entier non signé sur deux octets.  
  
 OBJECT\_TYPE\_I4  
 indique que l'objet est un entier signé de quatre octets.  
  
 OBJECT\_TYPE\_U4  
 indique que l'objet est un entier non signé de quatre octets.  
  
 OBJECT\_TYPE\_I8  
 indique que l'objet est un entier signé de huit\-octet.  
  
 OBJECT\_TYPE\_U8  
 indique que l'objet est un entier non signé de huit\-octet.  
  
 OBJECT\_TYPE\_R4  
 indique que l'objet est un nombre à virgule flottante de quatre octets.  
  
 OBJECT\_TYPE\_R8  
 indique que l'objet est un nombre à virgule flottante de huit\-octet.  
  
 OBJECT\_TYPE\_OBJECT  
 indique que l'objet est un objet.  
  
 OBJECT\_TYPE\_NULL  
 indique que l'objet est NULL.  
  
 OBJECT\_TYPE\_CLASS  
 indique que l'objet est une classe.  
  
## Notes  
 passé comme argument aux méthodes d' [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) et d' [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .  
  
## Configuration requise  
 en\-tête : ee.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)