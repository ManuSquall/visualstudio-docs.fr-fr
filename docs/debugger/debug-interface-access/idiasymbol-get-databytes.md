---
title: IDiaSymbol::get_dataBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203732d2ac222f4b4b74fa2e4c90f05b05754b47
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463959"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
Récupère les octets de données d’un symbole OEM.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_dataBytes ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Paramètres
 `cbData`

dans Taille de la mémoire tampon pour stocker les données.

 `pcbData`

à Retourne le nombre d’octets écrits ou, si le `data` paramètre a la valeur `NULL` , retourne le nombre d’octets disponibles.

 `data[]`
- [out,] Mémoire tampon qui est remplie avec les octets de données.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)