---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2da182992999a582ea30f570734b366178a9521
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464407"
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

à `DWORD`Pointeur de tableau qui est rempli avec les valeurs de balise de pointeur d’accélérateur dans la fonction stub d’accélérateur C++ amp.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="remarks"></a>Remarques
 Cette méthode est appelée sur une `IDiaSymbol` interface qui correspond à une C++ amp fonction stub d’accélérateur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)