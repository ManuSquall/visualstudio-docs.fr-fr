---
title: IDiaEnumSectionContribs::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e13f9290c76eb558bea397f7921f7cfd765613f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468092"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Ignore un nombre spécifié de contributions de section dans une séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Paramètres
 `celt`

dans Nombre de contributions de section dans la séquence d’énumération à ignorer.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` s’il n’y a plus de contribution de section à ignorer.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)