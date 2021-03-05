---
description: Spécifie si le mappage d’adresses doit être utilisé pour traduire les adresses de symboles.
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84878e83db15cfa5a9c68dccfec78536035cb70f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159513"
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

dans Affectez `TRUE` la valeur pour activer la traduction des symboles, ou `FALSE` pour désactiver.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les après-processeurs exécutables mettent parfois à jour l’exécutable. DIA contient un mécanisme qui permet de prendre en charge la traduction de symboles vers la nouvelle disposition.

 Lors du chargement d’un fichier PDB, le mappage d’adresses stocké dans le fichier est activé. Dans certains cas, toutefois, une application cliente peut avoir besoin de fournir son propre mappage d’adresses en appelant la méthode [IDiaAddressMap :: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Si la `set_addressMap` méthode réussit, l’application cliente doit appeler la `put_addressMapEnabled` méthode avec un `NewVal` paramètre `TRUE` pour permettre l’utilisation de ce mappage d’adresses.

 L’état actuel du mappage d’adresses en cours d’activation peut être récupéré à l’aide d’un appel à la méthode [IDiaAddressMap :: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
