---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36cf93beb6b6c8b66ec25dc8008be7024e398b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554337"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Spécifie si le mappage d’adresses doit être utilisé pour traduire les adresses de symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Paramètres
 NewVal

[in] La valeur `TRUE` pour activer la traduction de symboles, ou `FALSE` à désactiver.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Exécutables post-processeurs parfois mettre à jour que le fichier exécutable. DIA contient un mécanisme pour prendre en charge la traduction de symboles de la nouvelle disposition.

 Quand un fichier PDB est chargé, le mappage de l’adresse stocké dans le fichier est activé. Il existe, toutefois, une application cliente peut devez parfois fournir son propre mappage d’adresses en appelant le [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (méthode). Si le `set_addressMap` méthode est réussie, l’application cliente doit appeler le `put_addressMapEnabled` méthode avec un `NewVal` paramètre de `TRUE` pour activer l’utilisation de ce mappage d’adresses.

 L’état actuel de la carte d’adresse en cours d’activation peut être récupéré avec un appel à la [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) (méthode).

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)