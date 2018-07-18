---
title: IDiaSymbol::get_hasAlloca | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasAlloca method
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86e701f6b851b48345c9dcbcf3f2482d7c6c0951
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465523"
---
# <a name="idiasymbolgethasalloca"></a>IDiaSymbol::get_hasAlloca
Récupère un indicateur qui spécifie si la fonction contient un appel à `alloca` (qui est utilisé pour allouer de la mémoire sur la pile).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]HRESULT get_hasAlloca(   BOOL *pFlag);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si la fonction contient un appel à `alloca`; sinon, retourne `FALSE`.  
  
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