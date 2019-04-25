---
title: IDiaSymbol::get_isSingleInheritance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70b99b852175febe448e7b821070261d6abda4b9
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58947932"
---
# <a name="idiasymbolgetissingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie si le `this` pointeur pointe vers un membre de données avec l’héritage unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isSingleInheritance(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `BOOL` qui spécifie si le `this` pointeur pointe vers un membre de données avec l’héritage unique.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
