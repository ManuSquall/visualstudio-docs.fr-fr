---
title: "BasicType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BasicType (énumération)"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

spécifie le type de base du symbole.  
  
## Syntaxe  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Éléments  
 btNoType  
 aucun type de base n'est spécifié.  
  
 btVoid  
 le type de base est `void`.  
  
 btChar  
 Le type de base est `char` type \(C\/C\+\+\).  
  
 btWChar  
 Le type de base est un caractère large \(Unicode\) \(`WCHAR`\).  
  
 btInt  
 Le type de base est `signed int` type \(C\/C\+\+\).  
  
 btUInt  
 Le type de base est `unsigned int` type \(C\/C\+\+\).  
  
 btFloat  
 le type de base est un nombre à virgule flottante \(`FLOAT`\).  
  
 btBCD  
 Le type de base est un décimal encodée en binaire \(`BCD`\).  
  
 btBool  
 Le type de base est une valeur booléenne \(`BOOL`\).  
  
 btLong  
 Le type de base est `long int` type \(C\/C\+\+\).  
  
 btULong  
 Le type de base est `unsigned long int` type \(C\/C\+\+\).  
  
 btCurrency  
 Le type de base est devise.  
  
 btDate  
 le type de base est date\/heure \(`DATE`\).  
  
 btVariant  
 le type de base est une structure variable de type \(`VARIANT`\).  
  
 btComplex  
 Le type de base est un nombre complexe.  
  
 btBit  
 le type de base est un bit.  
  
 btBSTR  
 le type de base est une chaîne de base ou binaire \(`BSTR`\).  
  
 btHresult  
 le type de base est `HRESULT`.  
  
## Notes  
 Les valeurs de cette énumération sont retournées par la méthode d' [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## Configuration requise  
 en\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)