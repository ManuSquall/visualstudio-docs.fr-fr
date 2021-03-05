---
description: Permet au client d’activer ou de désactiver le calcul et l’utilisation des adresses virtuelles relatives (RVA).
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c3aab1379a39ee6abfd977350743e36c9792efb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158321"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Permet au client d’activer ou de désactiver le calcul et l’utilisation des adresses virtuelles relatives (RVA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Paramètres
 NewVal

dans Affectez la valeur `TRUE` pour activer ou `FALSE` Désactiver.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les adresses des objets de débogage décrits par les interfaces DIA et relatives à la base d’image de l’exécutable peuvent être récupérées en tant qu’adresses virtuelles relatives.

 L’utilisation des adresses RVA est activée lorsque les segments sont initialement chargés à partir d’un fichier PDB. Pour connaître l’état actuel de l’utilisation des adresses RVA, appelez la méthode [IDiaAddressMap :: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .

 La `put_relativeVirtualAddress` méthode doit être appelée pour activer les adresses RVA après un appel réussi à la méthode [IDiaAddressMap :: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) a établi de nouveaux en-têtes d’image.

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
