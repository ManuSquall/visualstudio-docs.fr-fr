---
title: IDiaSymbol::get_offset | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e1cf6b88a306fbb6cb127ec8174b5030a6d4d88
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465107"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
Récupère le décalage de l’emplacement de symboles. Quand utiliser le [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md) est `LocIsRegRel` ou `LocIsBitField`.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’offset en octets de l’emplacement de symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Le décalage est d’un point connu préalablement déterminé. Par exemple, le décalage pour un `LocIsBitField` type d’emplacement est généralement à partir du début de la classe conteneur.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType (énumération)](../../debugger/debug-interface-access/locationtype.md)