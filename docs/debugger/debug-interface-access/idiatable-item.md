---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738725"
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

dans Index de l’entrée de table dans la plage 0 à `count`-1, où `count` est retourné par la méthode [IDiaTable :: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

à Retourne un objet `IUnknown` qui représente l’entrée de table spécifiée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une table représente une collection d’objets. En fonction de ces objets, le paramètre d’élément peut être casté en interface appropriée. Par exemple, si une table contient des objets [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , le paramètre d’élément peut être casté en interface `IDiaSegment`.

 Une approche plus courante consiste à appeler la méthode `QueryInterface` dans l’interface [IDiaTable](../../debugger/debug-interface-access/idiatable.md) pour l’interface d’énumérateur appropriée et à utiliser les méthodes spécifiques de l’énumérateur pour accéder au contenu de la table. Pour obtenir un exemple, consultez l’interface [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>Voir aussi
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)