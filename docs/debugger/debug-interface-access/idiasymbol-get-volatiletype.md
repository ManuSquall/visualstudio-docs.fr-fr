---
title: IDiaSymbol::get_volatileType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5967a13596b5fad99f0f14277ea0e9505e222a41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738797"
---
# <a name="idiasymbolget_volatiletype"></a>IDiaSymbol::get_volatileType
Récupère un indicateur qui spécifie si le type de données défini par l’utilisateur (UDT) est volatile.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne `TRUE` si le type défini par l’utilisateur est volatile ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Dans C++, un UDT peut être marqué avec le mot clé `volatile`, indiquant que son contenu ne peut pas être supposé exister d’un accès à l’autre.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)