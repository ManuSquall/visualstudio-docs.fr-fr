---
title: IDiaSymbol::get_subType | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0b3cbf77-8f11-434a-ad60-ea9829fec6fa
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5eb3a65e635ba4785ccf2106f596ed20bbad178
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetsubtype"></a>IDiaSymbol::get_subType
Récupère le sous-type.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_subType(   
   IDiaSymbol** pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Pointeur vers le sous-type.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)