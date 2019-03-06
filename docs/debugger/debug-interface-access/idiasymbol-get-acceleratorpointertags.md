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
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607952"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Retourne toutes les valeurs de balise de pointeur accélérateur qui correspondent à une fonction de stub d’accélérateur C++ AMP.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Paramètres
 `cnt`

[in] La taille du tableau de sortie `pPointerTags`.

 `pcnt`

[out] Le nombre de balises de pointeur accélérateur dans la fonction de stub d’accélérateur C++ AMP.

 `pPointerTags`

[out] Un `DWORD` pointeur du tableau qui est rempli avec les valeurs de balise de pointeur accélérateur dans la fonction de stub d’accélérateur C++ AMP.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="remarks"></a>Remarques
 Cette méthode est appelée sur un `IDiaSymbol` interface qui correspond à une fonction de stub d’accélérateur C++ AMP.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)