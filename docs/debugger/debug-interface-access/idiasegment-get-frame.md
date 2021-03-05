---
description: Récupère le numéro de segment.
title: IDiaSegment::get_frame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_frame method
ms.assetid: 9fece9c7-064a-4d6b-9cef-fc387f322205
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f914002206f4b5ae5593fe3d4bd82c6a957ce1b4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159040"
---
# <a name="idiasegmentget_frame"></a>IDiaSegment::get_frame
Récupère le numéro de segment.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_frame ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le numéro de segment.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
