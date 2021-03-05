---
description: Retourne toutes les valeurs de balise de pointeur d’accélérateur qui correspondent à une fonction de stub d’accélérateur C++ AMP.
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bf6f90cb15484613a6572952a6f8501fa6bf31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156600"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Retourne toutes les valeurs de balise de pointeur d’accélérateur qui correspondent à une fonction de stub d’accélérateur C++ AMP.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Paramètres
 `cnt`

dans Taille du tableau de sortie `pPointerTags` .

 `pcnt`

à Nombre de balises de pointeur d’accélérateur dans la fonction stub d’accélérateur C++ AMP.

 `pPointerTags`

à `DWORD` Pointeur de tableau qui est rempli avec les valeurs de balise de pointeur d’accélérateur dans la fonction stub d’accélérateur C++ amp.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée sur une `IDiaSymbol` interface qui correspond à une C++ amp fonction stub d’accélérateur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
