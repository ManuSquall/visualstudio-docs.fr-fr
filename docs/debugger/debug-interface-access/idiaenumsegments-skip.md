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
ms.openlocfilehash: ff4c5d26d875dc098775d0d379e7d12b062801cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840016"
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

[in] Le nombre de segments dans la séquence d’énumération à ignorer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` si aucun segment plus à ignorer.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)