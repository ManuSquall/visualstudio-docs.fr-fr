---
title: IDiaSymbol::get_upperBound | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25ed8f3bcb1b4e8e2253dc1531bcdf8fd08be1e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021687"
---
# <a name="idiasymbolgetupperbound"></a>IDiaSymbol::get_upperBound
Récupère un symbole qui représente la limite supérieure d’une dimension de tableau FORTRAN.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_upperBound (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente la limite supérieure d’une dimension de tableau FORTRAN.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)