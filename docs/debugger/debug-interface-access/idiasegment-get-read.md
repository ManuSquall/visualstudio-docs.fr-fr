---
title: IDiaSegment::get_read | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_read method
ms.assetid: aafbc86d-352c-4e1a-911a-1472d2d59212
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 933a77e85a75cff3d846d0e28ff437039b32ffe9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637891"
---
# <a name="idiasegmentgetread"></a>IDiaSegment::get_read
Récupère un indicateur qui indique si le segment peut être lu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_read ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne `TRUE` si le segment peut être lue ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)