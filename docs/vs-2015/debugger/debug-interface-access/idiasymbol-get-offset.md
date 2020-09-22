---
title: IDiaSymbol::get_offset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f99a9cef4266be9a3373d20f09fca8c64e5a33b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839782"
---
# <a name="idiasymbolget_offset"></a>IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le décalage de l’emplacement du symbole. Utilisez lorsque l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md) est `LocIsRegRel` ou `LocIsBitField` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne le décalage en octets de l’emplacement du symbole.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Le décalage provient d’un point connu précédemment déterminé. Par exemple, le décalage d’un `LocIsBitField` type d’emplacement est généralement à partir du début de la classe conteneur.  
  
## <a name="requirements"></a>Spécifications  
  
|Condition requise|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
