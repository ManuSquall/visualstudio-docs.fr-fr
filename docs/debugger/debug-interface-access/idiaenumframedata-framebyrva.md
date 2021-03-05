---
description: Retourne un frame par adresse virtuelle relative (RVA).
title: IDiaEnumFrameData::frameByRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a11d249722f192232a80a8951e18e927f27e9a41
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159437"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Retourne un frame par adresse virtuelle relative (RVA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT frameByRVA( 
   DWORD           relativeVirtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Paramètres
 relativeVirtualAddress

dans Adresse RVA du cadre qui vous intéresse.

 frame

à Retourne un objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) représentant le frame qui contient l’adresse fournie.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si aucune donnée de frame ne correspond à l’adresse spécifiée. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
