---
description: Récupère l’emplacement dans la mémoire virtuelle de l’image.
title: IDiaImageData::get_virtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d958b8de0e7d200b4da7475cb37eb1dfa15fcf97
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157636"
---
# <a name="idiaimagedataget_virtualaddress"></a>IDiaImageData::get_virtualAddress
Récupère l’emplacement dans la mémoire virtuelle de l’image.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’adresse virtuelle de l’image.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
