---
description: Récupère un nombre spécifié de flux de débogage dans la séquence d’énumération.
title: IDiaEnumDebugStreams::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 645c04005263372df120f976e9dd402160594855
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158119"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Récupère un nombre spécifié de flux de débogage dans la séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG                     celt,
   IDiaEnumDebugStreamData** rgelt,
   ULONG*                    pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre de flux de débogage dans l’énumérateur à récupérer.

 rgelt

à Retourne un tableau d’objets [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) qui représente les flux de débogage en cours de récupération.

 pceltFetched

à Retourne le nombre de flux de débogage retournés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus de flux. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
