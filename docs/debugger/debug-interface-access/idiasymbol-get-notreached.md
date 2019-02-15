---
title: IDiaSymbol::get_isNaked | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_notReached method
ms.assetid: e44ba922-6cda-40c2-9b62-44e5a8628e63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3ef7418a232c5c6fa06062fbe6214f55e40b8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008528"
---
# <a name="idiasymbolgetnotreached"></a>IDiaSymbol::get_notReached
Récupère un indicateur qui spécifie si la fonction ou l’étiquette n’est jamais atteint.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_notReached(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pFlag  
 [out] Retourne `TRUE` si la fonction ou l’étiquette n’est jamais atteint ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)