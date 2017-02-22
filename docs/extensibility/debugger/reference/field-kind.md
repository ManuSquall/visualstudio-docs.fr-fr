---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "Énumération de FIELD_KIND"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie le type de champ contenu dans un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Syntaxe  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## Membres  
 FIELD\_KIND\_TYPE  
 Indique que le champ est un type uniquement.  
  
 FIELD\_KIND\_SYMBOL  
 Indique que le champ est un symbole, avec le type, name, et d'autres informations.  
  
 FIELD\_TYPE\_PRIMITIVE  
 Indique que le champ est un type de données primitives.  
  
 FIELD\_TYPE\_STRUCT  
 indique que le champ est une structure.  
  
 FIELD\_TYPE\_CLASS  
 Cela indique que le champ est une classe.  
  
 FIELD\_TYPE\_INTERFACE  
 Cela indique que le champ est une interface.  
  
 FIELD\_TYPE\_UNION  
 Cela indique que le champ est une union.  
  
 FIELD\_TYPE\_ARRAY  
 Indique que le champ est un tableau.  
  
 FIELD\_TYPE\_METHOD  
 indique que le champ est une méthode.  
  
 FIELD\_TYPE\_BLOCK  
 indique que le champ est un bloc.  
  
 FIELD\_TYPE\_POINTER  
 Cela indique que le champ est un pointeur.  
  
 FIELD\_TYPE\_ENUM  
 indique que le champ est un type de données énuméré.  
  
 FIELD\_TYPE\_LABEL  
 indique que le champ est un nom.  
  
 FIELD\_TYPE\_TYPEDEF  
 Cela indique que le champ est un typedef.  
  
 FIELD\_TYPE\_BITFIELD  
 indique que le champ est un champ de bits.  
  
 FIELD\_TYPE\_NAMESPACE  
 Cela indique que le champ est un espace de noms.  
  
 FIELD\_TYPE\_MODULE  
 indique que le champ est un module.  
  
 FIELD\_TYPE\_DYNAMIC  
 Cela indique que le champ est dynamique.  
  
 FIELD\_TYPE\_PROP  
 Cela indique que le champ est une propriété.  
  
 FIELD\_TYPE\_INNERCLASS  
 indique que le champ est une classe interne.  
  
 FIELD\_TYPE\_REFERENCE  
 Cela indique que le champ est une référence.  
  
 FIELD\_TYPE\_EXTENDED  
 Réservé à une utilisation future.  
  
 FIELD\_SYM\_MEMBER  
 indique que le champ est un membre.  
  
 FIELD\_SYM\_LOCAL  
 indique que le champ est local.  
  
 FIELD\_SYM\_PARAMETER  
 indique que le champ est un paramètre.  
  
 FIELD\_SYM\_THIS  
 Indique que le champ est le pointeur « this ».  
  
 FIELD\_SYM\_GLOBAL  
 indique que le champ est global.  
  
 FIELD\_SYM\_PROP\_GETTER  
 Cela indique que le champ récupère des propriétés.  
  
 FIELD\_SYM\_PROP\_SETTER  
 indique que le champ définit des propriétés.  
  
 FIELD\_SYM\_EXTENDED  
 Réservé à une utilisation future.  
  
 FIELD\_KIND\_MASK  
 Indique un masque pour les champs.  
  
 FIELD\_TYPE\_MASK  
 Indique un masque pour les champs.  
  
 FIELD\_SYM\_MASK  
 indique un masque pour les informations de symbole.  
  
## Notes  
 Retourné par un appel à la méthode d' [GetKind](../Topic/IDebugField::GetKind.md) .  
  
 Selon le type de champ, [QueryInterface](/visual-cpp/atl/queryinterface) peut être invité l'interface d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pour plus de formulaire spécifique d'interface.  Par exemple, si [GetKind](../Topic/IDebugField::GetKind.md) retourne `FIELD_TYPE_METHOD`, vous pouvez ensuite appeler `QueryInterface` sur I`DebugField` pour obtenir l'interface d' [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) .  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../Topic/IDebugField::GetKind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)