---
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
ms.openlocfilehash: 9eb951dd2362b93c61e835da78e5e02d6dc67069
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857040"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` s’il n’y a plus d’enregistrements. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)