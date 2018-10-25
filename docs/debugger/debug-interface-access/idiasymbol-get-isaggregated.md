---
title: IDiaSymbol::get_isAggregated | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isAggregated method
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e74c6f465676b916954141679406b00b9787347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941488"
---
# <a name="idiasymbolgetisaggregated"></a>IDiaSymbol::get_isAggregated
Récupère un indicateur qui spécifie si le symbole de données fait partie d’un agrégat ou une collection de symboles ; le compilateur traite les symboles agrégées comme des entités distinctes, mais elles font vraiment partie d’un symbole unique plus grand.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_isAggregated(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFlag`  
 [out] Retourne `TRUE` si les données font partie d’une agrégation de symboles fractionnées à partir d’un symbole parent ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Le [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) méthode est `TRUE` pour le symbole qui est le parent des symboles agrégées.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)