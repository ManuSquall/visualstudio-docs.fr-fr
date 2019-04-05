---
title: IDiaSymbol::get_isSdl | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da15e70cab420289e46b9e413aa0fe046b97671d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949056"
---
# <a name="idiasymbolgetissdl"></a>IDiaSymbol::get_isSdl
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie si le module est compilé avec l’option /SDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `BOOL` qui spécifie si le module est compilé avec l’option /SDL.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
