---
title: IDiaSegment::get_execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a2673880b80f229b05f5efba5c5dfb708aec0f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742446"
---
# <a name="idiasegmentget_execute"></a>IDiaSegment::get_execute
Récupère un indicateur qui signale si le segment est exécutable.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_execute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le segment est marqué comme exécutable ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)