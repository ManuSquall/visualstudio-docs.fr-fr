---
description: Récupère un nombre spécifié de segments dans la séquence d’énumération.
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 95d4ac6d566033472d7769e4a1a5df86cdf7ff70
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159229"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Récupère un nombre spécifié de segments dans la séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de segments dans l’énumérateur à récupérer.

 rgelt

à Tableau à remplir avec les objets [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) souhaités qui représentent les segments.

 pceltFetched

à Retourne le nombre de segments dans l’énumérateur extrait.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de segments. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
