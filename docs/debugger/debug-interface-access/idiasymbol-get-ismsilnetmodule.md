---
title: IDiaSymbol::get_isMSILNetmodule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isMSILNetmodule method
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df52c7a6a82bd24d3be51971b1d288b97d0b491a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627699"
---
# <a name="idiasymbolgetismsilnetmodule"></a>IDiaSymbol::get_isMSILNetmodule
Récupère un indicateur qui spécifie si le module est un fichier .netmodule (module en langage MSIL (Microsoft Intermediate Language) qui contient uniquement les métadonnées et aucun symbole natif).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isMSILNetmodule(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Paramètres
 `pFlag`

[out] Retourne `TRUE` si le module est MSIL ; sinon, retourne `FALSE`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="remarks"></a>Remarques
 Cette propriété est disponible à partir de la `SymTagCompilandDetails` type de symbole (consultez [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)).

## <a name="requirements"></a>Spécifications

|Spécification|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)