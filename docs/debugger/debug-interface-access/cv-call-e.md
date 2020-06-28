---
title: CV_call_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: afab1aef58616bfa925fd9f37aacf195eb569c96
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462140"
---
# <a name="cv_call_e"></a>CV_call_e
Spécifie la Convention d’appel d’une fonction.

> [!NOTE]
> Seules les valeurs d’énumération les plus courantes sont documentées ici. L’énumération complète est disponible dans le fichier d’en-tête cvconst. h.

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
CV_CALL_NEAR_C spécifie une convention d’appel de fonction utilisant un push proche de droite à gauche. La fonction appelante efface la pile.

CV_CALL_NEAR_FAST spécifie une convention d’appel de fonction utilisant un push proche de gauche à droite avec registres. La fonction appelée utilise la somme des octets de paramètres pour effacer la pile.

CV_CALL_NEAR_STD spécifie une convention d’appel de fonction à l’aide d’un appel near standard (push de droite à gauche).

CV_CALL_NEAR_SYS spécifie une convention d’appel de fonction à l’aide d’un appel near System.

CV_CALL_THISCALL spécifie une convention d’appel de fonction à l’aide `this` d’un appel ( `this` pointeur passé dans le registre).

CV_CALL_CLRCALL spécifie une convention d’appel de fonction utilisée par le Common Language Runtime (CLR) (également appelé Convention d’appel de code managé).

## <a name="remarks"></a>Remarques
Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
