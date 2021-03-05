---
description: Ignore un nombre spécifié de fichiers sources dans une séquence d’énumération.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1292329e20807b87eafc7ab98f4cfb226607d354
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159187"
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
