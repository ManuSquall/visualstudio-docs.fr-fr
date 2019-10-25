---
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4680af2d41ef3fa06a89784003c98982a09c2b63
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740351"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Récupère un indicateur qui spécifie si la fonction est une fonction virtuelle d’introduction.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
`pRetVal`

à Retourne `TRUE` si la fonction est virtuelle Intro ; Sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="example"></a>Exemple

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

@No__t_0 et `B::f1` sont des fonctions virtuelles, mais `A::f1` est une présentation virtuelle.

## <a name="requirements"></a>spécifications

|Exigence|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
