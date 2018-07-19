---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f5e6ceefbff4702d509c18b4a555287a1e9f42
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466641"
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