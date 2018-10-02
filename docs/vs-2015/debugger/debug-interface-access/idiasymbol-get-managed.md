---
title: IDiaSymbol::get_managed | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSymbol::get_managed method
ms.assetid: a69d00be-2a89-415c-b116-385c422e2fd5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 213c63048735570eda2572e8f10e1251cb83e849
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508483"
---
# <a name="idiasymbolgetmanaged"></a>IDiaSymbol::get_managed
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSymbol::get_managed](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-managed).  
  
Récupère un indicateur qui spécifie si le symbole fait référence au code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_managed (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne `TRUE` si le symbole fait référence au code managé ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



