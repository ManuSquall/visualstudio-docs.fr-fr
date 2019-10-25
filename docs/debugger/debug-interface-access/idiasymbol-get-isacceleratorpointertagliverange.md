---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5a24a136bb9c04366449a91d825ddbecff2957
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740326"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Récupère un indicateur qui signale si le symbole correspond au symbole de la *plage de définitions* du composant de la balise d’une variable pointeur dans C++ le code compilé pour un accélérateur amp. Le symbole de la plage de définition est l’emplacement d’une variable pour une plage d’adresses.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

à Pointeur vers une `BOOL` qui indique si le symbole correspond au symbole de la plage de définitions.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)