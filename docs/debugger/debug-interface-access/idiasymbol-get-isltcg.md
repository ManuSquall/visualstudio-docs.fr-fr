---
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7eb1d7308eb03d396ca8a08f915a294ec1debd82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877736"
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
Récupère un indicateur qui spécifie si le [Compiland](../../debugger/debug-interface-access/compiland.md) a été lié avec le commutateur de l’éditeur de liens [/LTCG (Link-time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation), qui facilite l’optimisation de l’ensemble du programme. Ce commutateur s’applique uniquement au code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_iSLTCG(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pFlag  
 [out] Retourne `TRUE` si le `compiland` a été lié avec le commutateur de l’éditeur de liens /LTCG ; sinon, retourne `FALSE`.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK 8.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)