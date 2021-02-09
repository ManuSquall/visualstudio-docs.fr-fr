---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 975321d9710e9b448fa0b6b860f76c2f0b84d52e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857159"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Permet de contrôler la façon dont le kit de développement logiciel (SDK) DIA calcule les adresses virtuelles et virtuelles pour les objets de débogage.

## <a name="syntax"></a>Syntaxe

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDiaAddressMap` .

|Méthode|Description|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Indique si un mappage d’adresses a été établi pour une session particulière.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Spécifie si le mappage d’adresses doit être utilisé pour traduire les adresses de symboles.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Indique si le calcul et l’utilisation des adresses virtuelles relatives sont activés.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Permet au client d’activer ou de désactiver le calcul d’adresses virtuelles relatives.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Récupère l’alignement de l’image actuelle.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Définit l’alignement de l’image.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Définit les en-têtes d’image pour activer la traduction d’adresses virtuelles relatives.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Fournit un mappage d’adresses pour prendre en charge les traductions de disposition d’image.|

## <a name="remarks"></a>Remarques
 Le contrôle fourni par cette interface est encapsulé dans deux jeux de données que vous fournissez : des en-têtes d’images et des mappages d’adresses. La plupart des clients utilisent la méthode [IDiaDataSource :: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) pour rechercher les informations de débogage appropriées pour une image et la méthode peut généralement découvrir tous les en-têtes nécessaires et mapper les données elles-mêmes. Toutefois, certains clients implémentent un traitement spécialisé et recherchent des données. Ces clients utilisent les méthodes de l' `IDiaAddressMap` interface pour fournir le kit de développement logiciel (SDK) dia avec les résultats de la recherche.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est disponible à partir de l’objet de session DIA. Le client appelle la `QueryInterface` méthode sur l’interface d’objet de session dia, généralement [IDiaSession](../../debugger/debug-interface-access/idiasession.md), pour récupérer l' `IDiaAddressMap` interface.

## <a name="requirements"></a>Configuration requise
 En-tête : Dia2. h

 Bibliothèque : diaguids. lib

 DLL : msdia80.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces (SDK Debug Interface Access)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)