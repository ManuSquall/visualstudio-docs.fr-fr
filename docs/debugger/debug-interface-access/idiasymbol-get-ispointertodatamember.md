---
title: IDiaSymbol::get_isPointerToDataMember | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a4f117ca9e19c932a56ab3a68caf457dfa0fe6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009256"
---
# <a name="idiasymbolgetispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
Spécifie si ce symbole est un pointeur vers un membre de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `BOOL` qui spécifie si ce symbole est un pointeur vers un membre de données.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)