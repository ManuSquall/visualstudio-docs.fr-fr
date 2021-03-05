---
description: Récupère un indicateur qui signale si le segment est exécutable.
title: IDiaSegment::get_execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: abb2ce313b33d81f4960ef22cc8946574cf5ea94
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159047"
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

à Retourne `TRUE` si le segment est marqué comme exécutable ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
