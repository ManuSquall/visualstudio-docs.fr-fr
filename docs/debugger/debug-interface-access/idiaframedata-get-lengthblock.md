---
title: IDiaFrameData::get_lengthBlock | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82f09b454b167fbba9ff267ed4293100162af237
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467322"
---
# <a name="idiaframedataget_lengthblock"></a>IDiaFrameData::get_lengthBlock
Récupère la longueur, en octets, du bloc de code décrit par le frame.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lengthBlock ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre d’octets de code dans le frame.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 La valeur retournée par cette méthode est généralement utilisée dans l’interprétation d’une chaîne de programme (consultez la méthode [IDiaFrameData :: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) pour la définition d’une chaîne de programme).

## <a name="see-also"></a>Voir aussi
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)