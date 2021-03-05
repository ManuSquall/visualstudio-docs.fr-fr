---
description: Retourne un frame par adresse virtuelle (VA).
title: IDiaEnumFrameData::frameByVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2fa167749574165df2a7acffdc232e3fd4c66e4a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158077"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Retourne un frame par adresse virtuelle (VA).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Paramètres
 virtualAddress

dans VA du cadre qui vous intéresse.

 frame

à Retourne un objet [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) qui représente le frame contenant l’adresse fournie.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si aucune donnée de frame ne correspond à l’adresse spécifiée. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
