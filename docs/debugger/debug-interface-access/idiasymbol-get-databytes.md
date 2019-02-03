---
title: IDiaSymbol::get_dataBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d70ede5bdade583d0b25787f7c97c345cef9cbe1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925355"
---
# <a name="idiasymbolgetdatabytes"></a>IDiaSymbol::get_dataBytes
Récupère les octets de données d’un symbole OEM.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbData`  
 [in] Taille de la mémoire tampon devant contenir les données.  
  
 `pcbData`  
 [out] Retourne le nombre d’octets écrits, ou, si le `data` paramètre est `NULL`, retourne le nombre d’octets disponibles.  
  
 `data[]`  
 [out] Une mémoire tampon est remplie avec les octets de données.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|Dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)