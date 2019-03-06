---
title: IDiaSymbol::get_machineType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10a645ff35c903d7d315719a63f8fed34a1b6011
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611280"
---
# <a name="idiasymbolgetmachinetype"></a>IDiaSymbol::get_machineType
Récupère le type de l’unité centrale cible.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_machineType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Retourne une valeur de la [CV_CPU_TYPE_e (énumération)](../../debugger/debug-interface-access/cv-cpu-type-e.md) énumération qui spécifie le type de processeur cible.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [CV_CPU_TYPE_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)