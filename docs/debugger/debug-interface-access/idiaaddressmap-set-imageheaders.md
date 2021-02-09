---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63bf56b7749033ecc99c7ba1ef0c9357c95542d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865278"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Définit les en-têtes d’image pour activer la traduction d’adresses virtuelles relative.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Paramètres
 cbData

dans Nombre d’octets de données d’en-tête. Doit être `n*sizeof(IMAGE_SECTION_HEADER)` où `n` est le nombre d’en-têtes de section dans l’exécutable.

 data[]

dans Tableau de  `IMAGE_SECTION_HEADER` structures à utiliser comme en-têtes d’image.

 originalHeaders

dans Affectez la valeur `FALSE` si les en-têtes d’image proviennent de la nouvelle image, `TRUE` s’ils reflètent l’image d’origine avant une mise à niveau. En règle générale, il est défini sur `TRUE` uniquement en association avec les appels à la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 La `IMAGE_SECTION_HEADER` structure est déclarée dans Winnt. h et représente le format d’en-tête de la section image de l’exécutable.

 Les calculs d’adresses virtuelles relatifs dépendent des `IMAGE_SECTION_HEADER` valeurs. En règle générale, le DIA les récupère à partir du fichier de base de données du programme (. pdb). Si ces valeurs sont manquantes, le DIA n’est pas en mesure de calculer des adresses virtuelles relatives et la méthode [IDiaAddressMap :: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) retourne `FALSE` . Le client doit ensuite appeler la méthode [IDiaAddressMap ::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) pour activer les calculs d’adresses virtuelles relatifs après avoir fourni les en-têtes d’image manquants à partir de l’image elle-même.

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)