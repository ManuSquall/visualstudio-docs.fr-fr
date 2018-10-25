---
title: THUNK_ORDINAL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: a92e0fa81bdfc7c33e790c5022c2fbe341d632be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847706"
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)