---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741113"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Retourne toutes les valeurs de balise de pointeur d' C++ accélérateur qui correspondent à une fonction de stub d’accélérateur amp.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Paramètres
 `cnt`

dans Taille du tableau de sortie `pPointerTags`.

 `pcnt`

à Nombre de balises de pointeur d’accélérateur C++ dans la fonction stub de l’accélérateur amp.

 `pPointerTags`

à Pointeur de tableau `DWORD` qui est rempli avec les valeurs de balise de pointeur C++ d’accélérateur dans la fonction stub d’accélérateur amp.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée sur une interface `IDiaSymbol` qui correspond à une C++ fonction de stub d’accélérateur amp.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)