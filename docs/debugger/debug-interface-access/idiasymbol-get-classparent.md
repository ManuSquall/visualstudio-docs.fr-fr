---
title: IDiaSymbol::get_classParent | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_classParent method
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3e96cbfb5c82ed9a07273ba6b75e4298dcb0d04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetclassparent"></a>IDiaSymbol::get_classParent
Récupère une référence au parent de la classe du symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_classParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le parent de la classe du symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="remarks"></a>Remarques  
 Les types de symboles qui peuvent être les parents de la classe sont documentées dans [hiérarchie de classe de Types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)