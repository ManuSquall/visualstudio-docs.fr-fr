---
description: Récupère une référence à l’entrée spécifiée dans la table.
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9693a1d16666dcb23f97d918807f9c2fea31c186
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161675"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Récupère une référence à l’entrée spécifiée dans la table.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Paramètres
 `index`

dans Index de l’entrée de table dans la plage de 0 à `count` -1, où `count` est retourné par la méthode [IDiaTable :: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

à Retourne un `IUnknown` objet qui représente l’entrée de table spécifiée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une table représente une collection d’objets. En fonction de ces objets, le paramètre d’élément peut être casté en interface appropriée. Par exemple, si une table contient des objets [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , le paramètre d’élément peut être casté en `IDiaSegment` interface.

 Une approche plus courante consiste à appeler la `QueryInterface` méthode dans l’interface [IDiaTable](../../debugger/debug-interface-access/idiatable.md) pour l’interface d’énumérateur appropriée et à utiliser les méthodes spécifiques de l’énumérateur pour accéder au contenu de la table. Pour obtenir un exemple, consultez l’interface [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
