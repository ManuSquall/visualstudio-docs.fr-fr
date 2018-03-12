---
title: IDiaAddressMap::set_addressMap | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 681e0bae46497d9b581e89340069937370831777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Fournit un mappage d’adresse pour prendre en charge les traductions de disposition d’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbData`  
 [in] Le nombre d’éléments dans le `data` paramètre.  
  
 `data[]`  
 [in] Un tableau de [diaaddressmapentry, Structure](../../debugger/debug-interface-access/diaaddressmapentry.md) structures qui définissent le mappage de conversion.  
  
 `imagetoSymbols`  
 [in] `TRUE` si le `data` paramètre définit un mappage à partir de la nouvelle disposition de l’image à la disposition d’origine (comme indiqué par les symboles de débogage). `FALSE`Si `data` est un mappage à la nouvelle disposition d’image obtenue à partir de la disposition d’origine.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En général, le DIA extrait les mappages de traduction d’adresse à partir du fichier de base de données (.pdb) de programme. Si ces valeurs sont manquantes, le [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) méthode est appelée à deux reprises, une fois avec le `imagetoSymbols` paramètre la valeur `TRUE` et une fois avec le `imagetoSymbols` paramètre la valeur `FALSE`. Mappage de conversion ne peut pas être activée à l’aide de la [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) (méthode), sauf si les deux tables de traduction sont fournis.  
  
## <a name="see-also"></a>Voir aussi  
 [Diaaddressmapentry, Structure](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)