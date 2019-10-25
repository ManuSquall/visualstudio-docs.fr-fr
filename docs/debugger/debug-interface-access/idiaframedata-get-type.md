---
title: IDiaFrameData::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4af060a4a0c36067a07a78166d1cf9cbc62e90e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743484"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Récupère le type de frame spécifique au compilateur.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne une valeur de l’énumération d' [énumération StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) qui indique le type de frame spécifique au compilateur.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [StackFrameTypeEnum, énumération](../../debugger/debug-interface-access/stackframetypeenum.md)