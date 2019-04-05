---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938257"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fournit un mappage d’adresses pour prendre en charge les traductions de disposition d’image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] `TRUE` si le `data` paramètre définit un mappage à partir de la nouvelle disposition de l’image à la disposition d’origine (comme indiqué par les symboles de débogage). `FALSE` Si `data` est un mappage de la nouvelle disposition d’image extraite de la disposition d’origine.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En règle générale, le DIA récupère les mappages de traduction d’adresse à partir du fichier de base de données (.pdb) de programme. Si ces valeurs sont manquantes, le [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) méthode est appelée à deux reprises, une fois avec le `imagetoSymbols` paramètre défini sur `TRUE` et une fois avec le `imagetoSymbols` paramètre défini sur `FALSE`. Mappage des traductions d’adresses ne peut pas être activées à l’aide de la [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) (méthode), sauf si les deux cartes de traduction sont fournies.  
  
## <a name="see-also"></a>Voir aussi  
 [DiaAddressMapEntry, structure](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
