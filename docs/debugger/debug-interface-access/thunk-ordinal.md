---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e139bceb9456e792ddf10d00d8b519a7677cc22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834059"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Désigne les types de conversion de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Éléments  
 THUNK_ORDINAL_NOTYPE  
 Conversion de code standard.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Un `this` thunk d’expert.  
  
 THUNK_ORDINAL_VCALL  
 Conversion de code d’appel virtuel.  
  
 THUNK_ORDINAL_PCODE  
 Thunk de P-code.  
  
 THUNK_ORDINAL_LOAD  
 Thunk de chargement différé.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Thunk trampoline incrémentielle (un thunk trampoline est utilisé pour retransmettre des appels à partir de l’espace mémoire d’un à un autre).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Conversion de code trampoline de point de branche.  
  
## <a name="remarks"></a>Notes  
 Les valeurs dans cette énumération sont retournées à partir d’un appel à la [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)