---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576406"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Désigne les types de thunks.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Thunk standard.  
  
 THUNK_ORDINAL_ADJUSTOR  
 `this`Thunk de réglage.  
  
 THUNK_ORDINAL_VCALL  
 Thunk d’appel virtuel.  
  
 THUNK_ORDINAL_PCODE  
 Thunk de code P.  
  
 THUNK_ORDINAL_LOAD  
 Thunk de chargement différé.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Thunk trampoline incrémentiel (un thunk trampoline est utilisé pour rebondir les appels d’un espace mémoire à un autre).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Thunk point de branche trampoline.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de cette énumération sont retournées à partir d’un appel à la méthode [IDiaSymbol :: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst. h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
