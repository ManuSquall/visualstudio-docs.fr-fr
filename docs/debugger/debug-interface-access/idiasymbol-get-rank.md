---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cff86464a4034ad869cdfe231a88ad128dbf52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739491"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Récupère le rang (nombre de dimensions) d’un tableau multidimensionnel FORTRAN.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nombre de dimensions dans un tableau multidimensionnel FORTRAN.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Notes
 Rank fait référence au nombre de dimensions dans un tableau où le tableau est déclaré comme `myarray[1,2,3]`. Cet exemple a un rang de 3 et 3 dimensions. Rank ne s’applique pas C++ à qui utilise le concept d’un tableau de tableaux pour chaque dimension (autrement dit, `myarray[1][2][3]`).

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)