---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf017d70400cee426598d0a99264596781cf898a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933267"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Retourne le nombre de balises de pointeur accélérateur dans une fonction de stub de C++ AMP.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `count`  
 [out] Un pointeur vers un `DWORD` qui contient le nombre d’accélérateur de balises de pointeur dans une fonction de stub de C++ AMP.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée sur un `IDiaSymbol` interface qui correspond à une fonction de stub d’accélérateur C++ AMP.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)