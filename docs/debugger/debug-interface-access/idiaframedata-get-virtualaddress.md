---
description: Récupère l’adresse virtuelle (VA) du code du frame.
title: IDiaFrameData::get_virtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_virtualAddress method
ms.assetid: de137bee-132f-4aae-a067-9578b7a3e6d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 048d78185450cb06be7265f4db0cf34cf1a2d5d2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157650"
---
# <a name="idiaframedataget_virtualaddress"></a>IDiaFrameData::get_virtualAddress
Récupère l’adresse virtuelle (VA) du code du frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’adresse virtuelle du code du frame.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
