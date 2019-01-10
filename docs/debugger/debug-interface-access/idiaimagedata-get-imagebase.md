---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0dea0b3e717187bb79525fde0be02d0482e53243
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912660"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Récupère l’emplacement de mémoire où l’image doit être basée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne la valeur de base d’image suggérée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En raison de conflits de base d’image, une image peut être redéfinie automatiquement vers un emplacement de mémoire inutilisée lorsqu’il est chargé. Cette méthode retourne l’indicateur de base (suggéré emplacement de mémoire) qui a été stocké dans le module au moment de la compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)