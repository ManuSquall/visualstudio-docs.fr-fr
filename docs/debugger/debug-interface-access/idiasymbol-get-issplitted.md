---
title: IDiaSymbol::get_isSplitted | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSplitted method
ms.assetid: ff160cf6-003b-4ef5-a406-20a7b287b2bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15c30577900a2d2e192bdc2dea45fc89846b102b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919325"
---
# <a name="idiasymbolgetissplitted"></a>IDiaSymbol::get_isSplitted
Récupère un indicateur qui spécifie si le symbole de données a été divisé en une agrégation ou une collection d’autres symboles ; le compilateur traite les symboles en tant qu’entités distinctes, même si elles font vraiment partie d’un symbole plus volumineux.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_isSplitted(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si le symbole a été divisé en un agrégat de symboles ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Le [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md) retourne de la méthode `TRUE` pour tous les symboles qui font partie d’un symbole de fractionnement.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)