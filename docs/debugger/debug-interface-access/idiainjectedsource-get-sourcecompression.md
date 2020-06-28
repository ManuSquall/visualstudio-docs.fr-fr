---
title: IDiaInjectedSource::get_sourceCompression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e32450e355d757081efaf66e7c5abaf179e7fd95
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467021"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Récupère l’indicateur de la compression source utilisé.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne l’indicateur de la compression source utilisé. La valeur zéro indique qu’aucune compression source n’a été utilisée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 La valeur retournée par cette méthode est spécifique au compilateur utilisé. Par exemple, un compilateur peut utiliser l’encodage de longueur d’exécution ou la compression de style Huffman.

## <a name="see-also"></a>Voir aussi
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)