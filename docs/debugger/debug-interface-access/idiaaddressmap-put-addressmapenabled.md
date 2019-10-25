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
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745065"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Spécifie si le mappage d’adresses doit être utilisé pour traduire les adresses de symboles.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Paramètres
 NewVal

dans Affectez la valeur `TRUE` pour activer la traduction des symboles, ou `FALSE` à désactiver.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Les après-processeurs exécutables mettent parfois à jour l’exécutable. DIA contient un mécanisme qui permet de prendre en charge la traduction de symboles vers la nouvelle disposition.

 Lors du chargement d’un fichier PDB, le mappage d’adresses stocké dans le fichier est activé. Dans certains cas, toutefois, une application cliente peut avoir besoin de fournir son propre mappage d’adresses en appelant la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Si la méthode `set_addressMap` est réussie, l’application cliente doit appeler la méthode `put_addressMapEnabled` avec un paramètre `NewVal` de `TRUE` pour permettre l’utilisation de ce mappage d’adresses.

 L’état actuel du mappage d’adresses en cours d’activation peut être récupéré à l’aide d’un appel à la méthode [IDiaAddressMap :: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)