---
title: IDiaEnumSourceFiles::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6dd38782a7618259d802ae898c643d2a504c3fc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467875"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
Ignore un nombre spécifié de fichiers sources dans une séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de fichiers sources dans la séquence d’énumération à ignorer.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` s’il n’y a plus de fichiers sources à ignorer.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)