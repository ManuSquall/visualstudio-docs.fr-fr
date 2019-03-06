---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac6a7582c6fa59665390cfdb6b613fff6e36709
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644677"
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Récupère un indicateur qui indique si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour un accélérateur de l’AMP C++.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

[out] Un pointeur vers un `BOOL` qui indique si le symbole correspond à une variable locale partagée de groupe dans le code compilé pour un accélérateur de l’AMP C++. Si `TRUE`, le `get_baseDataSlot` et `get_baseDataOffset` méthodes peuvent être utilisées pour obtenir les informations d’emplacement de stockage pour la variable.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)