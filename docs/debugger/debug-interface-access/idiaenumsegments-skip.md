---
title: IDiaEnumSegments::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efedd0e24c96259f1c9e9b6fc7522ee250bd4b25
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744166"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Ignore un nombre spécifié de segments dans une séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de segments dans la séquence d’énumération à ignorer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` s’il n’y a plus de segments à ignorer.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)