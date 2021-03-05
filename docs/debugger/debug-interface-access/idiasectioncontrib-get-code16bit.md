---
description: Récupère un indicateur qui signale si la section contient du code 16 bits.
title: IDiaSectionContrib::get_code16bit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee13c8a67498cf8aadb0f498d1b392112ece9c5c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157314"
---
# <a name="idiasectioncontribget_code16bit"></a>IDiaSectionContrib::get_code16bit
Récupère un indicateur qui signale si la section contient du code 16 bits.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_code16bit(
   BOOL *pRetVal
};
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le code dans la section est 16 bits ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode indique uniquement si le code est 16 bits. Si le code n’est pas 16 bits, il peut s’agir d’autres éléments, tels que le code 32 bits ou 64 bits.

## <a name="see-also"></a>Voir aussi
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
