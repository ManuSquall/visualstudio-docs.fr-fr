---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3122c5a237b28ee9e5c4aea9aa8f36de639c2875
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
 [out] Un pointeur vers un `DWORD` , qui contient le nombre d’accélérateur balises de pointeur à une fonction de stub de C++ AMP.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée sur une `IDiaSymbol` interface qui correspond à une fonction de stub d’accélérateur C++ AMP.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)