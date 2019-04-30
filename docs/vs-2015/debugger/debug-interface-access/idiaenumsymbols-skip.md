---
title: IDiaEnumSymbols::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7a6a3f06572392cad2edbf125d0ff6491b508c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563700"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Ignore un nombre spécifié de symboles dans une séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Paramètres
 celt

[in] Le nombre de symboles dans la séquence d’énumération à ignorer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` s’il n’existe plus aucun symbole à ignorer.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)