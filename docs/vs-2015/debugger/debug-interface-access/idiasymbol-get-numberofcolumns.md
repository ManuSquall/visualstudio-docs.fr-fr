---
title: IDiaSymbol::get_numberOfColumns | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 64834351-e2c9-4f1c-9dc0-2abb5478bc63
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d389e34e8028961e2769c04a6c4a2561bcd0729
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938508"
---
# <a name="idiasymbolgetnumberofcolumns"></a>IDiaSymbol::get_numberOfColumns
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le nombre de colonnes dans la matrice.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_numberOfColumns(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `DWORD` qui contient le nombre de colonnes dans la matrice.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
