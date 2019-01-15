---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b13669c7a93141f3b54c15a20a5faee43d5a8747
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953207"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Récupère le type de conversion de code d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne une valeur de la [THUNK_ORDINAL (énumération)](../../debugger/debug-interface-access/thunk-ordinal.md) énumération qui spécifie le type de conversion de code d’une fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est valide uniquement si le symbole comme un [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeur `SymTagThunk`.  
  
 Une conversion de « code » est un morceau de code qui effectue la conversion entre un espace d’adressage de mémoire de 32 bits (également appelé espace d’adresse plat) et un espace d’adressage de 16 bits (appelé un espace d’adressage segmentés).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL, énumération](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)