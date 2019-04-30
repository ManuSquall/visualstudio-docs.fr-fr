---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5fea99994b891250dad85cfc43320848df98f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555102"
---
# <a name="cvcalle"></a>CV_call_e
Spécifie la convention d’appel pour une fonction.

> [!NOTE]
> Seules les valeurs d’énumération courants sont décrits ici. L’énumération complète est disponible dans le fichier d’en-tête cvconst.h.

## <a name="syntax"></a>Syntaxe

```C++
typedef enum CV_call_e {
    CV_CALL_NEAR_C    = 0x00,
    CV_CALL_NEAR_FAST = 0x04,
    CV_CALL_NEAR_STD  = 0x07,
    CV_CALL_NEAR_SYS  = 0x09,
    CV_CALL_THISCALL  = 0x0b,
    CV_CALL_CLRCALL   = 0x16
} CV_call_e;
```

## <a name="elements"></a>Éléments
CV_CALL_NEAR_C spécifie une convention d’appel de fonction à l’aide d’un push proche de droite à gauche. La fonction appelante efface la pile.

CV_CALL_NEAR_FAST spécifie une convention d’appel de fonction à l’aide de gauche à droite quasi push avec inscrit. La fonction appelée utilise la somme des octets de paramètre pour effacer la pile.

CV_CALL_NEAR_STD spécifie une convention d’appel de fonction via un appel standard quasiment (push de droite à gauche).

CV_CALL_NEAR_SYS spécifie une convention d’appel de fonction à l’aide d’un système quasi appeler.

CV_CALL_THISCALL spécifie une à l’aide de la convention d’appel de fonction `this` appeler (`this` pointeur passé dans le Registre).

CV_CALL_CLRCALL spécifie une convention d’appel de fonction utilisée par le Common Language Runtime (CLR) (également appelé un code managé convention d’appel).

## <a name="remarks"></a>Notes
Les valeurs dans cette énumération sont retournées par un appel à la [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) (méthode).

## <a name="requirements"></a>Configuration requise
En-tête : cvconst.h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
