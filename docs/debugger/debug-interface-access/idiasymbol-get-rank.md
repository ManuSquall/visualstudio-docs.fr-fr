---
title: IDiaSymbol::get_rank | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 623c700c6f9a30b6142faeb7e1b31881d0e0fe11
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Récupère le rang (nombre de dimensions) d’un tableau multidimensionnel FORTRAN.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre de dimensions dans un tableau multidimensionnel FORTRAN.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Rang fait référence au nombre de dimensions dans un tableau où le tableau est déclaré en tant que `myarray[1,2,3]`. Cet exemple a le rang 3 et 3 dimensions. Rang ne s’applique pas à C++ qui utilise le concept d’un tableau de tableaux pour chaque dimension (autrement dit, `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)