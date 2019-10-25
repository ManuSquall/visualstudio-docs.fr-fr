---
title: IDiaSegment::get_length | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_length method
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74b4e0d96013504a0fd03b7350c58f1987903ad0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742418"
---
# <a name="idiasegmentget_length"></a>IDiaSegment::get_length
Récupère le nombre d’octets dans le segment.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_ length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre d’octets dans le segment.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)