---
title: THUNK_ORDINAL | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2711ab101299b47e954e56fcbbae98d9f5fdb6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Désigne les types de conversion de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
typedef enum THUNK_ORDINAL {   
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
 A `this` thunk d’expert.  
  
 THUNK_ORDINAL_VCALL  
 Conversion de code d’appel virtuel.  
  
 THUNK_ORDINAL_PCODE  
 Conversion de code P-code.  
  
 THUNK_ORDINAL_LOAD  
 Thunk de chargement différé.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Conversion de code trampoline incrémentielle (un thunk trampoline sert rebondit des appels à partir de l’espace de mémoire à un autre).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Conversion de code trampoline de point de branche.  
  
## <a name="remarks"></a>Remarques  
 Les valeurs de cette énumération sont retournées à partir d’un appel à la [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)