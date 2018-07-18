---
title: IDiaSymbol::get_oemId | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6911e617a8cac136eb7b51913db48fbb031803d4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465120"
---
# <a name="idiasymbolgetoemid"></a>IDiaSymbol::get_oemId
Récupère la valeur d’ID du symbole fabricant (OEM).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_oemId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne une valeur unique qui identifie un fabricant OEM.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Cette propriété s’applique uniquement aux symboles avec un [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) le type de `SymTagCustomType`.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)