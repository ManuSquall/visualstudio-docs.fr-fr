---
title: IDiaSymbol::get_hasEH | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_hasEH method
ms.assetid: 9a4952d8-9fa7-4798-b48c-fe4357648276
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b27bcb0cc3f74d4d99d8bbe4dedf5b7f48b6e9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgethaseh"></a>IDiaSymbol::get_hasEH
Récupère un indicateur qui spécifie si la fonction contient toutes les exceptions style C++ non managée (par exemple, un bloc try/catch).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_hasEH(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si la fonction a toutes les exceptions de style C++ ; sinon, retourne `FALSE`.  
  
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