---
description: Récupère un nombre spécifié d’enregistrements dans la séquence énumérée.
title: IDiaEnumDebugStreamData::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e854a4bbcd7c1429ef14a90f705f80afc92e75bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159452"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Récupère un nombre spécifié d’enregistrements dans la séquence énumérée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>Paramètres
 celt

dans Nombre d’enregistrements à récupérer.

 cbData

dans Taille de la mémoire tampon de données, en octets.

 pcbData

à Retourne le nombre d’octets retournés. Si `data` a la valeur null, `pcbData` contient le nombre total d’octets de données disponibles pour tous les enregistrements demandés.

 data[]

à Mémoire tampon qui doit être remplie avec les données de l’enregistrement de flux de débogage.

 pceltFetched

[in, out] Retourne le nombre d’enregistrements dans `data` .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus d’enregistrements. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
