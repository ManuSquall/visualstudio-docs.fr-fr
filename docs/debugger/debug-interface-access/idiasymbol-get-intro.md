---
description: Récupère un indicateur qui spécifie si la fonction est une fonction virtuelle d’introduction.
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad2e791995f4edc1b09655640bc339d577f7f37d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160875"
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

à Retourne `TRUE` si la fonction est virtuelle Intro ; sinon, retourne `FALSE` .

## <a name="return-value"></a>Valeur renvoyée
En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou code d’erreur.

> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="example"></a>Exemple

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

`A::f1`Et `B::f1` sont des fonctions virtuelles, mais `A::f1` il s’agit d’une présentation virtuelle.

## <a name="requirements"></a>Configuration requise

|Condition requise|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 7.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
