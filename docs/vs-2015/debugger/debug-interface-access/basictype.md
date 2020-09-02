---
title: BasicType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580835"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie le type de base du symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="elements"></a>Éléments  
 btNoType  
 Aucun type de base n’est spécifié.  
  
 btVoid  
 Le type de base est `void` .  
  
 btChar  
 Le type de base est un `char` (type C/C++).  
  
 btWChar  
 Le type de base est un caractère étendu (Unicode) ( `WCHAR` ).  
  
 btInt  
 Le type de base est `signed int` (type C/C++).  
  
 btUInt  
 Le type de base est `unsigned int` (type C/C++).  
  
 btFloat  
 Le type de base est un nombre à virgule flottante ( `FLOAT` ).  
  
 btBCD  
 Le type de base est un décimal codé binaire ( `BCD` ).  
  
 btBool  
 Le type de base est un booléen ( `BOOL` ).  
  
 btLong  
 Le type de base est un `long int` (type C/C++).  
  
 btULong  
 Le type de base est un `unsigned long int` (type C/C++).  
  
 btCurrency  
 Le type de base est Currency.  
  
 btDate  
 Le type de base est Date/Time ( `DATE` ).  
  
 btVariant  
 Le type de base est une structure de type variable ( `VARIANT` ).  
  
 btComplex  
 Le type de base est un nombre complexe.  
  
 btBit  
 Le type de base est un peu.  
  
 btBSTR  
 Le type de base est une chaîne de base ou binaire ( `BSTR` ).  
  
 btHresult  
 Le type de base est `HRESULT` .  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées par la méthode [IDiaSymbol :: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol :: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
