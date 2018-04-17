---
title: IDiaImageData::get_imageBase | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 032ff3cee51c3c8295395aba6e9e60bfa4e9a400
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
 En raison de conflits de base d’image, une image peut être redéfinie automatiquement vers un emplacement de la mémoire inutilisée quand il est chargé. Cette méthode retourne l’indicateur de base (emplacement recommandée pour la mémoire) qui a été enregistrée dans le module au moment de la compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)