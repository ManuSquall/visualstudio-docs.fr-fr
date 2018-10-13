---
title: IDiaSymbol::get_count | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_count method
ms.assetid: f6d6ac2f-6d96-4f88-962b-29c0a66890b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5acc7cce205a3eb08c07ce20d0606762ffcfc5f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299453"
---
# <a name="idiasymbolgetcount"></a>IDiaSymbol::get_count
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le nombre d’éléments dans une liste ou un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_count (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre d’éléments dans une liste ou un tableau.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



