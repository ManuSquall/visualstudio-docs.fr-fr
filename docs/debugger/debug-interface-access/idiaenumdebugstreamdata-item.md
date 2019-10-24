---
title: IDiaEnumDebugStreamData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e221516198d186dd08c353123ce4236f0be1383c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744820"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
Récupère l’enregistrement spécifié.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD  index,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Paramètres
 index

dans Index de l’enregistrement à récupérer. L’index se trouve dans la plage 0 à `count`-1, où `count` est retourné par [IDiaEnumDebugStreamData :: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md).

 cbData

dans Taille de la mémoire tampon de données, en octets.

 cbData

à Retourne le nombre d’octets retournés. Si `data` est `NULL`, `pcbData` contient le nombre total d’octets de données disponibles dans l’enregistrement spécifié.

 data[]

à Mémoire tampon qui est renseignée avec les données de l’enregistrement de flux de débogage.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur. Retourne `E_INVALIDARG` pour les paramètres non valides et si le paramètre `index` est hors limites.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)