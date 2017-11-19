---
title: IDiaSymbol::get_restrictedType | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 294afc254ee9f08e21019d08354fdecb5c05c1f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetrestrictedtype"></a>IDiaSymbol::get_restrictedType
Spécifie si le `this` pointeur soit marqué comme restreint.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_restrictedType(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `BOOL` qui spécifie si le `this` pointeur soit marqué comme restreint.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)