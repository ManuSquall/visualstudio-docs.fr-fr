---
title: IDiaSymbol::get_isPointerToMemberFunction | Microsoft Docs
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
ms.assetid: aa9b5599-9602-41be-ab50-d84b90bee72f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b1c6115811989a319713cf67ac529c9e022498
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508725"
---
# <a name="idiasymbolgetispointertomemberfunction"></a>IDiaSymbol::get_isPointerToMemberFunction
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaSymbol::get_isPointerToMemberFunction](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction).  
  
Spécifie si ce symbole est un pointeur vers une fonction membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isPointerToMemberFunction(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `BOOL` qui spécifie si ce symbole est un pointeur vers une fonction membre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



