---
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e03c01efb9f2dca13009a7dc7eeb8282b5c9082c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468043"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Récupère un segment au moyen d’un index.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’objet [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) à récupérer. L’index se trouve dans la plage de 0 à `count` -1, où `count` est retourné par la méthode [IDiaEnumSegments :: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) .

 segment

à Retourne un objet [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) représentant le segment souhaité.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)