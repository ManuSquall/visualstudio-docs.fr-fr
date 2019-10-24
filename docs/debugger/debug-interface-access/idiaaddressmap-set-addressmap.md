---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745026"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Fournit un mappage d’adresses pour prendre en charge les traductions de disposition d’image.

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

dans Nombre d’éléments dans le paramètre `data`.

 `data[]`

dans Tableau de structures de [structure DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) qui définissent le mappage de la traduction.

 `imagetoSymbols`

[in] `TRUE` si le paramètre `data` définit une carte de la nouvelle disposition d’image à la disposition d’origine (comme décrit par les symboles de débogage). `FALSE` si `data` est une carte à laquelle la nouvelle disposition d’image provient de la disposition d’origine.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 En règle générale, le DIA récupère les mappages de traduction d’adresses à partir du fichier de base de données du programme (. pdb). Si ces valeurs sont manquantes, la méthode [IDiaAddressMap :: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) est appelée deux fois, une fois avec le paramètre `imagetoSymbols` défini sur `TRUE` et une fois avec le paramètre `imagetoSymbols` défini sur `FALSE`. Les traductions de mappage d’adresses ne peuvent pas être activées à l’aide de la méthode [IDiaAddressMap ::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , sauf si les deux mappages de traduction sont fournis.

## <a name="see-also"></a>Voir aussi
- [DiaAddressMapEntry, structure](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)