---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "Énumération de FIELD_MODIFIERS"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Spécifie les modificateurs d'un type de champ.  
  
## Syntaxe  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## Membres  
 FIELD\_MOD\_ACCESS\_TYPE  
 Cela indique que le champ est impossible.  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 indique que le champ a accès public.  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 Cela indique que le champ protégé l'accès.  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 Cela indique que le champ a un accès privé.  
  
 FIELD\_MOD\_NOMODIFIERS  
 indique que le champ n'a aucun modificateur.  
  
 FIELD\_MOD\_STATIC  
 indique que le champ est statique.  
  
 FIELD\_MOD\_CONSTANT  
 Cela indique que le champ est une constante.  
  
 FIELD\_MOD\_TRANSIENT  
 indique que le champ est transitoire.  
  
 FIELD\_MOD\_VOLATILE  
 Indique que le champ est volatile.  
  
 FIELD\_MOD\_ABSTRACT  
 Cela indique que le champ est abstrait.  
  
 FIELD\_MOD\_NATIVE  
 indique que le champ est natif.  
  
 FIELD\_MOD\_SYNCHRONIZED  
 Cela indique que le champ est synchronisé.  
  
 FIELD\_MOD\_VIRTUAL  
 Cela indique que le champ est virtuel.  
  
 FIELD\_MOD\_INTERFACE  
 Cela indique que le champ est une interface.  
  
 FIELD\_MOD\_FINAL  
 indique que le champ est final.  
  
 FIELD\_MOD\_SENTINEL  
 indique que le champ est une sentinelle.  
  
 FIELD\_MOD\_INNERCLASS  
 indique que le champ est une classe interne.  
  
 FIELD\_TYPE\_OPTIONAL  
 indique que le champ est facultatif.  
  
 FIELD\_MOD\_BYREF  
 indique que le champ est un argument de référence.  Il s'agit spécifiquement pour les arguments de méthode.  
  
 FIELD\_MOD\_HIDDEN  
 indique que le champ doit être masqué ou présenté dans un autre contexte ; par exemple, les variables locales de statique de [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 indique que le champ représente un objet avec une interface d' `IUnknown` .  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 Indique que le champ a un nom spécial, par exemple, `.ctor` pour un constructeur \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] uniquement\).  
  
 FIELD\_MOD\_HIDEBYSIG  
 Indique que le champ a le mot clé d' `Overloads` appliqué à une \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] uniquement\).  
  
 FIELD\_MOD\_WRITEONLY  
 indique que le champ est en écriture seule.  Cette valeur n'est pas inclus dans `FIELD_MOD_ALL`, car la seule utilisation de ces champs en écriture seule est pour l'évaluation de fonction.  Un utilisateur doit demander explicitement les champs d' `FIELD_MOD_WRITEONLY` .  
  
 FIELD\_MOD\_ACCESS\_MASK  
 Indique un masque pour l'accès au champ.  
  
 FIELD\_MOD\_MASK  
 Indique un masque pour les modificateurs de champ.  
  
## Notes  
 utilisé pour le membre d' `dwModifiers` de la structure de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
 ces valeurs sont également passées à la méthode d' [EnumFields](../Topic/IDebugContainerField::EnumFields.md) au filtre pour les champs spécifiques.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../Topic/IDebugContainerField::EnumFields.md)