---
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fe43b99ce430e1e06683494fdeb1c5716b30cea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Retourne le début de la plage d’adresses dans lequel le symbole local est valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_liveRangeStartRelativeVirtualAddress (   
   DWORD* address  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [out] Retourne le début de la plage d’adresses.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. L’adresse virtuelle relative retourné est le début de la plage dans laquelle le symbole est valide.  
  
> [!NOTE]
>  Un code d’erreur signifie que le symbole n’a pas d’informations sur la plage dynamique.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia100.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)