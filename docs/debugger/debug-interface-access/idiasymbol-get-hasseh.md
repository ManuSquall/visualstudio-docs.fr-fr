---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ced9377d017bfbbcb4a200c004f8223a5636f39
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925578"
---
# <a name="idiasymbolgethasseh"></a>IDiaSymbol::get_hasSEH
Récupère un indicateur qui spécifie si la fonction contient un [structurée des exceptions (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) (par exemple, __try /\__except blocs).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si la fonction a tout structurée des exceptions blocs ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Gestion structurée des exceptions (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)